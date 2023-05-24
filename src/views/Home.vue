<template>
  <div class="home">
    <MainBanner/>

    <Advantages />
  </div>

</template>

<script>
import MainBanner from "@/components/MainBanner";
import Advantages from "@/components/Advantages";

export default {
  name: 'HomeView',
  components: {
    Advantages,
    MainBanner
  }
}
</script>
