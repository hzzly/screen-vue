<template>
  <v-card :title="title">
    <div slot="content" class="contentWrap">
      <div class="label" v-for="(item, index) in data" :key="index">
        <div :class="['icon iconfont', item.icon ? `icon-${item.icon}` : '']"></div>
        <div class="msg">
          <span>{{item.count}}</span>
          <span>{{item.label}}</span>
        </div>
      </div>
    </div>
  </v-card>
</template>

<script>

import VCard from '@/components/Card'

export default {
  name: 'Property',
  components: {
    VCard
  },
  data () {
    return {
      title: '物业信息',
      data: [{
        label: '保安',
        count: 14,
        icon: 'baoan'
      }, {
        label: '保洁',
        count: 20,
        icon: 'baojie'
      }, {
        label: '维修工',
        count: 2,
        icon: 'weixiugong'
      }, {
        label: '服务台',
        count: 5,
        icon: 'fuwutai'
      }]
    }
  }
}
</script>

<style lang="scss" scoped>
.contentWrap {
  width: 100%;
  height: 100%;
  display: flex;
  .label {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    .icon {
      font-size: 28px;
    }
    .msg {
      display: flex;
      flex-direction: column;
      text-align: center;
      margin-left: .3rem;
      span {
        font-size: 18px;
        &:last-child {
          font-size: 10px;
          color: #d7daed;
        }
      }
    }
  }
}
</style>


