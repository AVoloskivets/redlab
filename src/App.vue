<template :class="classMobile">
  <div :class="classMobile">
    <component :is="layout"></component>

    <router-view/>

    <OrderButton/>
  </div>
</template>
<script>
import '@/assets/fonts.css';
import Header from "@/components/Header";
import OrderButton from "@/components/OrderButton";
import HeaderMobile from "@/components/Header-mobile";

export default {
  components: {HeaderMobile, OrderButton, Header},
  data: () => ({
    isLargeScreen: true
  }),
  computed: {
    classMobile(){
      return this.$isMobile() ? 'mobile-app' : 'desktop-app'
    },
    layout(){
      return (this.$isMobile() || this.isLargeScreen === false) ? 'HeaderMobile' : 'Header'
    }
  },
  methods: {
    checkScreenWidth() {
      this.isLargeScreen = window.innerWidth >= 1280;
    }
  },
  mounted() {
    this.checkScreenWidth();
    window.addEventListener('resize', this.checkScreenWidth);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.checkScreenWidth);
  }
}
</script>

<style lang="scss">

body{
  margin: 0;
  color: #404040;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
a{
  text-decoration: none;
  color: #404040;
  transition: 0.3s ease;
  &:hover{
    color: #8A9924 !important;
  }
}
</style>
