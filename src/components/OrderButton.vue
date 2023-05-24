<template>
  <div
      class="elementMove"
      ref="elementMove"
      @mouseenter="initializeCursorPosition"
      @mousemove="trackCursorPosition"
      @mouseover="resetButton"
  >
    <button
        v-if="show"
        ref="button"
        @click="order"
        @mouseover="animateButton(true)"
        @mouseout="animateButton(false)">
      <span>{{ title }}</span>
    </button>
  </div>
</template>

<script>
import { gsap } from 'gsap';

export default {
  name: "OrderButton",
  data: () => ({
    show: true,
    title: "Замовити доставку",
    scrollTop: 0,
    screenHeight: window.innerHeight,
    prevX: 0,
    prevY: 0,
    elementMove: null
  }),
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.elementMove = this.$refs.elementMove
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    animateButton(isHover) {
      const button = this.$refs.button;
      if (isHover) {
        gsap.to(button, { y: 0, scale: this.$isMobile() ? 1 : 1.2, duration: 0.3 });
      }else if(this.scrollTop >= this.screenHeight / 3){
        gsap.to(button, { y: this.$isMobile() ? 30 : 80, scale: this.$isMobile() ? 0.6 : 0.3, duration: 0.3 });
      } else {
        gsap.to(button, { y: 0, scale: 1, duration: 0.3 });
      }
    },
    handleScroll() {
      const button = this.$refs.button;
      this.scrollTop = window.pageYOffset || document.documentElement.scrollTop;

      if(this.scrollTop >= this.screenHeight / 3){
        gsap.to(button, { y: this.$isMobile() ? 30 : 80, scale: this.$isMobile() ? 0.6 : 0.3, duration: 0.3 });
      }else {
        gsap.to(button, { y:0, scale: 1, duration: 0.3 });
      }
    },
    initializeCursorPosition(event) {
      this.prevX = event.clientX;
      this.prevY = event.clientY;
    },
    trackCursorPosition(event) {
      const currentX = event.clientX;
      const currentY = event.clientY;

      if (currentX > this.prevX) {
        // right
        gsap.to(this.elementMove, {x: 5, duration: 0.8});
      } else if (currentX < this.prevX) {
        // Left
        gsap.to(this.elementMove, {x: -5, duration: 0.8});
      }

      if (currentY > this.prevY) {
        // Down
        gsap.to(this.elementMove, {y: 5, duration: 0.8});

      } else if (currentY < this.prevY) {
        // Up
        gsap.to(this.elementMove, {y: -5, duration: 0.8});

      }

      this.prevX = currentX;
      this.prevY = currentY;
    },
    resetButton(){
      gsap.to(this.elementMove, {x: 0, y: 0, duration: 0.8});
    },
    order(){
      alert('Замовлення')
    }
  }
}
</script>

<style lang="scss" scoped>
  .elementMove{
    position: fixed;
    bottom: 16px;
    left: 50%;
    transform: translateX(-50%);

  }
  button{
    background: #5A30F0;
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    width: 195px;
    height: 195px;
    cursor: pointer;

    font-family: 'TT Travels';
    font-style: normal;
    font-weight: 600;
    font-size: 18px;
    line-height: 130%;
    color: #ffffff;

    display: flex;
    align-items: center;
    text-align: center;
    letter-spacing: 0.03em;
    text-transform: uppercase;
    span{
      animation: sway 2s infinite;
    }
    @media screen and (max-width: 920px) {
      width: 130px;
      height: 130px;
      font-size: 14px;
    }
  }

  @keyframes sway {
    0% {
      transform: rotate(-45deg);
    }
    50% {
      transform: rotate(+45deg);
    }
    100% {
      transform: rotate(-45deg);
    }
  }
</style>