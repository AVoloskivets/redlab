<template>
  <header>
    <div class="wrap">
      <div class="logo_wrap">
        <a href="/"><img src="../assets/images/FoodDeliver.svg" alt=""></a>
        <Switcher onText="Доставка" offText="Самовивіз"/>
      </div>
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
  </header>
</template>

<script>
import Switcher from "@/components/UI/Switcher";
export default {
  name: "Header",
  components: {Switcher},
  props:{
    menu:{
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  header{
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
    width: 100%;
    position: absolute;
    left: 0;
    top: 0;
    .logo_wrap{
      padding-left: 30px;
      display: flex;
      align-items: center;
      a{
        margin-right: 42px;
      }
    }
  }
  nav{
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    a{
      padding: 0 16px;
      font-family: 'TT Travels';
      font-style: normal;
      font-weight: 500;
      font-size: 16px;
      line-height: 120%;
    }
  }
  .info{
    font-family: 'TT Travels';
    font-style: normal;
    font-weight: 600;
    font-size: 16px;
    line-height: 120%;
    letter-spacing: 0.2px;
    a{
      color: inherit;
      text-decoration: none;
    }
  }
</style>