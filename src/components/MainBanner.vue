<template>
  <div class="main_banner">
    <div class="main_banner__bg" :style="`background-image: url(${images})`"></div>
    <div class="main_banner__content">
      <div class="main_banner__content_wrap">
        <h1>{{ title }}</h1>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import image from '@/assets/images/logan-jeffrey.jpg'

export default {
  name: "main-banner",
  data: () => ({
    title: "Доставка\n готової їжі у Києві",
    description: "Ми пропонуємо доставку їжі прямо до ваших дверей. Насолоджуйтесь смачними стравами без необхідності готувати самостійно.",
    images: image
  }),
}
</script>

<style lang="scss" scoped>
.main_banner{
  display: flex;
  height: 100vh;
  max-height: 800px;
  max-width: 1920px;
  margin: 0 auto;
  .main_banner__bg{
    flex: 0 1 50%;
    background-repeat: no-repeat;
    background-position: center;
    @media screen and (max-width: 768px) {
      flex: 0 1 30%;
    }
  }
  .main_banner__content{
    flex: 0 1 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    @media screen and (max-width: 768px) {
      flex: 1;
      position: relative;
    }
    .main_banner__content_wrap{
      max-width: 401px;
      text-align: left;
      margin-top: -10px;
      padding: 0 40px;
      @media screen and (max-width: 550px) {
        background: #ffffff;
        position: absolute;
        left: -25%;
        top: 50%;
        transform: translateY(-50%);
        padding: 0 20px 0 40px;
        max-width: 330px;
        //border: 1px solid #575054;
      }
      @media screen and (max-width: 550px) {
        left: -30%;
        padding: 0 20px 0 25px;

      }
      h1{
        font-family: 'TT Travels';
        font-style: normal;
        font-weight: 400;
        font-size: 76px;
        line-height: 110%;
        margin-bottom: 30px;
        @media screen and (max-width: 1024px) {
          font-size: 52px;
        }
        @media screen and (max-width: 768px) {
          font-size: 44px;
        }
        @media screen and (max-width: 550px) {
          font-size: 36px;
          margin-bottom: 19px;
        }
        @media screen and (max-width: 375px) {
          font-size: 28px;
        }
      }
      p{
        font-family: 'TT Travels';
        font-style: normal;
        font-weight: 400;
        font-size: 18px;
        line-height: 140%;
        @media screen and (max-width: 375px) {
          font-size: 17px;
        }
      }
    }
  }
}

</style>