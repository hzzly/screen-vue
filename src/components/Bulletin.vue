<template>
  <v-card :title="title">
    <div slot="legends">
      <div class="lengend" v-for="(item, index) in legendsValues" :key="index">
        <span :style="{backgroundColor: item.color}"></span>
        <span>{{item.label}}</span>
      </div>
    </div>
    <div slot="content" class="contentWrap">
      <div class="message" v-for="(item, index) in messagesValues" :key="index" :style="{backgroundColor: index % 2 === 0 ? '#181c49' : ''}">
        <span :style="{backgroundColor: item.color}"></span>
        <div :style="{color: item.color}">{{item.text}}</div>
      </div>
    </div>
  </v-card>
</template>

<script>

import VCard from '@/components/Card'

export default {
  name: 'Bulletin',
  components: {
    VCard
  },
  data () {
    return {
      title: '小区公告',
      legends: {
        2: {
          level: 2,
          label: '突发事件',
          color: '#E84A51'
        },
        1: {
          level: 1,
          label: '告示',
          color: '#F8D664'
        },
        0: {
          level: 0,
          label: '信息',
          color: '#D4E4F0'
        }
      },
      messages: [
        {
          id: 126,
          level: 0,
          text: '因配合轨道交通一号线人民街站建设迁移水管线，小区于9月12'
        },
        {
          id: 125,
          level: 1,
          text: '周五早上19号楼走廊烟雾报警器鸣响测试！'
        },
        {
          id: 124,
          level: 1,
          text: '严禁燃放烟花爆竹'
        },
        {
          id: 123,
          level: 1,
          text: '9月13日65岁以上老年免费体检公告'
        },
        {
          id: 122,
          level: 0,
          text: '上海市气象台13日10时发布暴雨红色预警，预计未来3小时内'
        },
        {
          id: 121,
          level: 0,
          text: '菜篮子工程将于本周开始进入小区'
        },
        {
          id: 120,
          level: 0,
          text: '本周五将对小区燃气管道进行检修'
        }
      ]
    }
  },
  computed: {
    legendsValues () {
      return Object.values(this.legends).reverse()
    },
    messagesValues () {
      return this.messages.slice(0, 7).map(e => ({
        ...e,
        color: this.legends[e.level].color
      }))
    }
  }
}
</script>

<style lang="scss" scoped>
span {
  font-size: 10px;
  color: #d7daed;
  &:first-child {
    width: .5rem;
    height: .5rem;
    border-radius: 50%;
    margin-right: .3rem;
  }
}
.lengend {
  float: right;
  margin-right: .95rem;
  span {
    display: inline-block;
  }
}
.contentWrap {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: .75rem .5rem 0 .5rem;
  overflow: hidden;
  .message {
    flex: 1;
    padding: 0 1rem;
    display: flex;
    align-items: center;
    overflow: hidden;
    font-size: 10px;
    div {
      flex: 1;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      width: 300px;
    }
  }
}
</style>


