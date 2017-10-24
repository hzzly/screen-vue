<template>
  <v-card :title="title">
    <div slot="legends" class="legends">
      <v-tab :tabs="tabsValue" :current="current" @onClick="onClick"></v-tab>
    </div>
    <div slot="content" class="contentWrap">
      <component v-bind:is="currentView" :componentDate="componentDate"></component>
    </div>
  </v-card>
</template>

<script>

import VTab from '@/components/Tab'
import VCard from '@/components/Card'

import HouseCard from './HouseCard'
import TrafficCard from './TrafficCard'

const COMPONENTS = {
  house: HouseCard,
  // people: PeopleCard,
  traffic: TrafficCard
  // safe: SafeCard,
}

const TRAFFIC = [360, 321, 322, 317, 295, 268, 211, 154, 127, 99, 101, 109, 138, 127, 100, 114, 120, 178, 177, 214, 241, 252, 262, 286]

const TOTAL = 400

export default {
  name: 'Resource',
  components: {
    VTab,
    VCard
  },
  data () {
    return {
      title: '社区信息',
      current: 'house',

      dataValues: {
        safe: {
          key: 'safe',
          label: '安全',
          abstruct: [{
            label: '社区盗窃率',
            extra: '市盗窃率: 0.2%',
            count: '0%'
          }, {
            label: '社区儿童老人走失',
            extra: '全市统计: 122起',
            count: '0起'
          }, {
            label: '周边交通事故',
            count: '2起'
          }],
          title: 13,
          subTitle: '社区出警次数',
          data: [{
            color: 'transparent',
            name: '类型',
            value: '近半年发生次数'
          }, {
            color: '#279AE7',
            name: '儿童老人走失',
            value: 0
          }, {
            color: '#4CCEC7',
            name: '小区车辆刮蹭',
            value: 4
          }, {
            color: '#A5E2A4',
            name: '社区邻里纠纷',
            value: 9
          }, {
            color: '#FED138',
            name: '严重暴力犯罪',
            value: 0
          }, {
            color: '#E84A51',
            name: '其他',
            value: 0
          }]
        },

        house: {
          key: 'house',
          label: '房源',
          title: 57,
          subTitle: '可用房源',
          data: [{
            name: '待租',
            value: 36
          }, {
            name: '待售',
            value: 12
          }, {
            name: '闲置',
            value: 9
          }]
        },

        people: {
          key: 'people',
          label: '人员',
          abstruct: [{
            label: '总户数',
            count: '700户'
          }, {
            label: '常驻人口',
            count: '2100人'
          }, {
            label: '流动人口数',
            count: '201人'
          }],
          title: 209,
          subTitle: '今日外来人次',
          data: [{
            color: 'transparent',
            name: '类型',
            value: '人数',
            averageStopTime: '平均停留时间'
          }, {
            color: '#FF2827',
            name: '访客',
            value: 86,
            averageStopTime: '24m'
          }, {
            color: '#279AE7',
            name: '外卖快递',
            value: 63,
            averageStopTime: '8m'
          }, {
            color: '#32C99F',
            name: '中介',
            value: 27,
            averageStopTime: '21m'
          }, {
            color: '#A5E2A4',
            name: '服务保障',
            value: 22,
            averageStopTime: '12m'
          }, {
            color: '#FED138',
            name: '其他',
            value: 11,
            averageStopTime: '20m'
          }]
        },

        traffic: {
          key: 'traffic',
          label: '车辆',
          abstruct: [{
            label: '车辆',
            count: TOTAL
          }, {
            label: '已占用',
            count: TRAFFIC.slice(0, new Date().getHours() + 1).pop()
          }, {
            label: '剩余',
            count: TOTAL - TRAFFIC.slice(0, new Date().getHours() + 1).pop()
          }],
          data: [{
            name: '已占用',
            // data: TRAFFIC.slice(0, new Date().getHours() + 1)
            data: TRAFFIC.slice(0, 24)
          }, {
            name: '可使用',
            // data: TRAFFIC.slice(0, new Date().getHours() + 1).map(e => TOTAL - e)
            data: TRAFFIC.slice(0, 24).map(e => TOTAL - e)
          }]
        }
      }
    }
  },
  methods: {
    onClick (e) {
      this.current = e.key
    }
  },
  computed: {
    options () {
      return this.dataValues[this.current]
    },
    tabsValue () {
      const tabsValue = Object.values(this.dataValues)
      return tabsValue
    },
    currentView () {
      return COMPONENTS[this.current]
    },
    componentDate () {
      return this.dataValues[this.current]
    }
  }
}
</script>

<style lang="scss" scoped>
.legends {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.contentWrap {
  width: 100%;
  height: 100%;
  // padding: .75rem .5rem 0 .5rem;
  overflow: hidden;
}
</style>


