<template>
  <div class="indexPage">
    <div class="herderWrap">
      <v-header :title="title" :indexes="indexes"></v-header>
    </div>
    <div class="mapWrap"></div>
    <div class="bulletinWrap"></div>
    <div class="propertyWrap"></div>
    <div class="resourceWrap"></div>
  </div>
</template>

<script>

import VHeader from '@/components/Header'

export default {
  components: {
    VHeader
  },
  data () {
    return {
      title: '智慧社区',
      indexes: [
        {name: '绿化', value: '32%'},
        {name: '噪音', value: 55.1},
        {name: '温度', value: '29C'},
        {name: '天气', value: '晴'}
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.indexPage {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(3,1fr);
  grid-template-rows: 50px repeat(3,1fr) 100px repeat(3,1fr);
  grid-gap: 6px;
  padding: 6px;
  color: #37d1ff;
  .herderWrap {
    grid-area: 1/1/span 1/span 3;
  }
  .mapWrap {
    grid-area: 2/1/span 7/span 2;
    background: #0d0f40;
    // min-height: 100%;
  }
  .bulletinWrap {
    grid-area: 2/3/span 3/span 1;
    background: #0d0f40;
  }
  .propertyWrap {
    grid-area: 5/3/span 1/span 1;
    background: #0d0f40;
  }
  .resourceWrap {
    grid-area: 6/3/span 3/span 1;
    background: #0d0f40;
  }
}
</style>


