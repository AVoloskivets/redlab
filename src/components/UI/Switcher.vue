<template>
  <div
      :class="{ 'on': status }"
      class="switcher">
    <span @click="switcher(false, $event.target)">Доставка</span>
    <span @click="switcher(true, $event.target)">Самовивіз</span>

    <span class="sw" :style="{ width: elementWidth }"></span>
  </div>
</template>

<script>
export default {
  name: "Switcher",
  props: {
    onText: {
      type: String,
      required: true
    },
    offText: {
      type: String,
      required: true
    }
  },
  data: () => ({
    status: false,
    elementWidth: '95px'
  }),
  methods:{
    switcher(flag, targetElement){
      const width = targetElement.offsetWidth;
      this.elementWidth = `${width}px`
      this.status = flag
    }
  }
}
</script>

<style lang="scss" scoped>
.switcher{
  background: #FFFFFF;
  border: 1px solid #E2E8F0;
  border-radius: 48px;
  height: 34px;
  display: flex;
  align-items: center;
  position: relative;
  max-width: 210px;
  width: 100%;
  .sw{
    background: #5A30F0;
    border-radius: 34px;
    position: absolute;
    left: 1px;
    top: 1px;
    width: 95px;
    height: calc(100% - 2px);
    padding: 0;
    z-index: 1;
    transition: left 0.8s, right 0.8s;
  }
  &.on{
    span{
      &:first-child{
        color: #636C81;
      }
      &:nth-child(2){
        color: #fff;
      }
    }
    .sw{
      right: 1px;
      left: 100px;
    }
  }
  span{
    font-family: 'TT Travels';
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
    line-height: 110%;
    color: #636C81;
    padding: 8px 12px;
    cursor: pointer;
    z-index: 2;
    &:not(.sw) {
      transition: color 0.5s;
    }
    &:first-child{
      margin-right: 6px;
      color: #ffffff;
    }
  }
}
</style>