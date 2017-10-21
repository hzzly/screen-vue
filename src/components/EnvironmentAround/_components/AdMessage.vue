<template>
  <div class="adMessage">
    <div class="title">{{adMessageTitle}}</div>
    <div class="content">
      <div class="row" v-for="(item, index) in adMessages" :key="index">
        <span>{{item.name}}</span>
        <span>{{item.status}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AdMessage',
  props: {
    adMessageTitle: {
      type: String
    },
    adMessages: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
.adMessage {
  color: #D7DAED;
  font-size: 10px;
  text-align: left;
  .title {
    padding: .5rem 0;
    font-size: 12px;
  }
  .content {
    .row {
      display: flex;
      flex-direction: column;
      padding: .35rem 0;
      span {
        &:first-child {
          margin-bottom: .5rem;
        }
        &:last-child {
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
      }
    }
  }
}
</style>


