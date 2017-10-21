<template>
  <div class="card">
    <div class="head">
      <div class="title"></div>
      <slot name="legends"></slot>
    </div>
    <div class="content">
      <slot name="content"></slot>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  padding: 1rem .5rem;
  .head {
    display: flex;
    justify-content: space-between;
    font-size: 18px;
  }
  .content {
    flex: 1 1 0%;
  }
}
</style>



