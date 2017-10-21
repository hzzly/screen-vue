<template>
  <div class="address">
    <div class="row">
      <span>{{position.name}}</span>
      <span>{{position.distance}}</span>
    </div>
    <div class="row">
      <span>{{position.level}}</span>
      <span>{{position.status}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Address',
  props: {
    position: {
      type: Object
    }
  }
}
</script>

<style lang="scss" scoped>
.address {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .row {
    display: flex;
    justify-content: space-between;
    margin: 0.2rem 1rem;
    font-size: 12px;
    color: #d7daed;
    &:first-child {
      border-bottom: 1px solid #25376a;
      padding-bottom: .2rem;
      font-size: 14px;
    }
    &:last-child {
      font-weight: 300;
    }
    span {
      &:last-child {
        color: #37d1ff;
        font-weight: 300;
        font-size: 12px;
      }
    }
  }
}
</style>


