<template>
  <div class="indexPage">
    <div class="herder"></div>
    <div class="map"></div>
    <div class="bulletin"></div>
    <div class="property"></div>
    <div class="resource"></div>
  </div>
</template>

<script>
export default {

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
  .header {
    grid-area: 1/1/span 1/span 3;
  }
  .map {
    grid-area: 2/1/span 7/span 2;
    background: #0d0f40;
    // min-height: 100%;
  }
  .bulletin {
    grid-area: 2/3/span 3/span 1;
    background: #0d0f40;
  }
  .property {
    grid-area: 5/3/span 1/span 1;
    background: #0d0f40;
  }
  .resource {
    grid-area: 6/3/span 3/span 1;
    background: #0d0f40;
  }
}
</style>


