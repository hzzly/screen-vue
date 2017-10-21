<template>
  <div class="indexPage">
    <div class="herderWrap">
      <v-header :title="title" :indexes="indexes"></v-header>
    </div>
    <div class="mapWrap">
      <div class="text">未来云栖 - 3D图</div>
      <div class="environmentWrap">
        <v-environment></v-environment>
      </div>
    </div>
    <div class="bulletinWrap"></div>
    <div class="propertyWrap"></div>
    <div class="resourceWrap"></div>
  </div>
</template>

<script>

import VHeader from '@/components/Header'
import VEnvironment from '@/components/EnvironmentAround'

export default {
  components: {
    VHeader,
    VEnvironment
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
    position: relative;
    background: url(../assets/bg.jpg) center center no-repeat;
    background-size: cover;
    .text {
      position: absolute;
      color: #37d1ff;
      font-size: 16px;
      padding: 1rem;
      z-index: 1001;
    }
    .environmentWrap {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      height: 200px;
      background: rgba(13, 23, 62, .8);
      padding: 1rem;
      display: flex;
      flex-direction: column;
    }
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


