<template>
  <div class="message">
    <div class="title">{{messageTitle}}</div>
    <div class="content">
      <div class="row" v-for="(item, index) in messages" :key="index">
        <div class="icon">{{item.icon}}</div>
        <div class="msg">{{item.text}}</div>
        <div class="msg">{{item.status}}</div>
        <div class="msg">{{item.schedule}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Message',
  props: {
    messageTitle: {
      type: String
    },
    messages: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
.message {
  color: #D7DAED;
  font-size: 10px;
  text-align: left;
  .title {
    padding: .5rem;
    font-size: 12px;
  }
  .content {
    .row {
      display: flex;
      padding: .35rem 0 .35rem .5rem;
      min-height: 2rem;
      .icon {
        width: 40px;
        // text-align: center;
      }
      .msg {
        flex: 1;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  }
}
</style>


