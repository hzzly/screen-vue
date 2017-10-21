<template>
  <div class="card">
    <div class="head">
      <div class="title">{{title}}</div>
      <slot name="legends"></slot>
    </div>
    <div class="content">
      <slot name="content"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    title: {
      type: String
    }
  }
}
</script>


<style lang="scss" scoped>
.card {
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  padding: 1rem .5rem;
  overflow: hidden;
  .head {
    display: flex;
    justify-content: space-between;
    font-size: 18px;
  }
  .content {
    flex: 1;
  }
}
</style>



