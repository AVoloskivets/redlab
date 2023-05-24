<template>
  <div class="header_wrap">
    <header>
      <div class="wrap">
        <div class="logo_wrap">
          <a href="/"><img src="../assets/images/FoodDeliver.svg" alt=""></a>
        </div>

        <div class="info">
          <a href="tel:+380674519957">+380 67 451 99 57</a>
          <button @click="toggleDrawer" class="open-drawer" style="z-index: 10"></button>
        </div>
      </div>
    </header>
    <Switcher onText="Доставка" offText="Самовивіз"/>

    <div :class="['drawer', { 'drawer-open': isOpen }]">
      <button @click="toggleDrawer" class="close-button"></button>
      <nav>
        <router-link
            v-for="link in menu"
            :key="link.url"
            :to="link.url"
            :exact="link.exact"
        >{{ link.title }}</router-link>
      </nav>
      <div class="info">
        <a href="tel:+380674519957">+380 67 451 99 57</a> | 24/7
      </div>
    </div>
  </div>

</template>

<script>
import Switcher from "@/components/UI/Switcher";

export default {
  name: "Header-mobile",
  components: {Switcher},
  props:{
    menu:{
      type: Array,
      required: true
    }
  },
  data: () => ({
    isOpen: false
  }),
  methods: {
    toggleDrawer() {
      this.isOpen = !this.isOpen;
    }
  }
}
</script>

<style lang="scss" scoped>
.header_wrap{
  width: 100%;
  position: absolute;
  left: 0;
  top: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 2;
}
header{
  width: 100%;
  .wrap{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16px;
    max-width: 1380px;
    width: 100%;
    position: relative;
  }
  display: flex;
  justify-content: center;
  align-items: center;

  .logo_wrap{
    display: flex;
    align-items: center;
    a{
      margin-right: 42px;
    }
  }
}
nav{
  margin-top: 30px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  a{
    padding: 0 16px;
    font-family: 'TT Travels';
    font-style: normal;
    font-weight: 500;
    font-size: 22px;
    line-height: 120%;
    margin-bottom: 20px;
  }
}
.info{
  font-family: 'TT Travels';
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 120%;
  letter-spacing: 0.2px;
  display: flex;
  align-items: center;
  a{
    color: inherit;
    text-decoration: none;
  }
}
.drawer {
  position: fixed;
  top: 0;
  right: -300px;
  width: 300px;
  height: 100%;
  background-color: #fff;
  transition: right 0.3s ease-in-out;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  text-align: left;
  z-index: 9999;
  .info{
    margin-top: 30px;
    border-top: 1px solid #35363A;
    padding-top: 20px;
    display: block;
    text-align: center;
  }
}
.drawer-open {
  right: 0;
}
.close-button {
  margin-top: 10px;
  background-image: url(../assets/images/cancel.png);
  border: none;
  width: 20px;
  height: 20px;
  background-position: center;
  background-size: cover;
  margin-left: 15px;
  background-color: transparent;
}
.open-drawer{
  background-image: url(../assets/images/menu.png);
  border: none;
  width: 24px;
  height: 24px;
  background-position: center;
  background-size: cover;
  margin-left: 15px;
  background-color: transparent;
}
</style>
