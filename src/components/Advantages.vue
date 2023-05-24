<template>
  <div class="advantages" ref="elementToShow">
    <div
        v-for="item in advantages"
        class="advantages__item"
    >
      <h4>{{ item.title }}</h4>
      <img :src="item.image" :alt="item.title">

      <div class="desc">{{ item.description }}</div>
    </div>
  </div>
</template>

<script>
import Bowl from '@/assets/images/advantages/Bowl.svg'
import Check from '@/assets/images/advantages/Check.svg'
import Clock from '@/assets/images/advantages/Clock.svg'
import Roket from '@/assets/images/advantages/Roket.svg'

import { gsap } from 'gsap';

export default {
  name: "Advantages",
  data: () => ({
    advantages: [
      {title: "Висока \n якість\n продукції", description: "Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.", image: Check},
      {title: "Різноманітність страв", description: "Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.", image: Bowl},
      {title: "Швидка доставка", description: "Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.", image: Roket},
      {title: "Працюємо цілодобово", description: "Наша доставка гарантує вам високу якість продуктів.  Кожна страва, яку ми готуємо, пройшла строгий контроль якості, щоб забезпечити вам найкращий смаковий досвід.", image: Clock}
    ],
    advantage_i: null
  }),
  mounted() {
    window.addEventListener('scroll', this.handleScroll);

    this.advantage_i = this.$refs.elementToShow.querySelectorAll('.advantages__item')
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    async handleScroll() {
      const element = this.$refs.elementToShow;
      const rect = element.getBoundingClientRect();

      if (rect.top <= window.innerHeight) {
        this.advantage_i.forEach((element, index) => {
          const delay = (index + 1) * 200;
          this.addClassWithDelay(element, 'my-class', delay);
        });

        // remove event scroll
        window.removeEventListener('scroll', this.handleScroll);
      }
    },
    addClassWithDelay(element, className, delay) {
      setTimeout(() => {
        element.classList.add(className);

        gsap.to(element, {marginTop: 0, duration: 0.4});
      }, delay);
    }
  }
}
</script>

<style lang="scss" scoped>
  .advantages{
    max-width: 1320px;
    margin: 73px auto;
    display: flex;
    @media screen and (max-width: 920px) {
      flex-wrap: wrap;
    }
    @media screen and (max-width: 550px) {
      flex-direction: column;
      align-items: center;
      margin: 45px auto;
    }
    .advantages__item{
      flex: 1;
      background: #F3F6FB;
      margin: 35px 20px 0;
      padding: 20px 40px;
      border-radius: 8px;
      position: relative;
      overflow: hidden;
      @media screen and (max-width: 1300px) {
        padding: 20px;
        margin: 35px 10px 0;
        h4{
          font-size: 22px;
        }
      }
      @media screen and (max-width: 920px) {
        flex: 0 0 calc(50% - 25px);
        box-sizing: border-box;
        margin-bottom: 20px;
      }
      @media screen and (max-width: 550px) {
        flex: 1;
        max-width: 290px;
        width: 100%;
        margin: 2px 20px 20px;
      }
      &:hover{
        img{
          opacity: 0;
        }
        .desc{
          transform: translateY(0);
        }
      }
      h4{
        margin: 0 0 20px;
        font-family: 'TT Travels';
        font-style: normal;
        font-weight: 500;
        font-size: 24px;
        line-height: 130%;
        text-align: center;
        @media screen and (max-width: 1300px) {
          font-size: 22px;
        }
      }
      img{
        opacity: 1;
        transition: opacity 0.5s ease-in-out;
        @media screen and (max-width: 1300px) {
          width: 160px;
        }
      }
      .desc{
        transition: transform 0.8s ease-in-out;
        transform: translateY(100%);
        position: absolute;
        top: 0;
        left: 0;
        height: calc(100% - 60px);
        padding: 30px;
        font-family: 'TT Travels';
        text-align: left;
        font-style: normal;
        font-weight: 400;
        font-size: 16px;
        line-height: 140%;
        color: #FFFFFF;
        background: #5A30F0;
        border-radius: 8px;
      }
    }
  }
</style>