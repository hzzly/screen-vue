<template>
  <div class="environment">
    <v-tab :tabs="tabsValue" :current="current" @onClick="onClick"></v-tab>
    <div class="component">
      <component v-bind:is="currentView" :componentDate="componentDate"></component>
    </div>
  </div>
</template>

<script>

import VTab from './Tab'

import Bus from './Bus'
import Rail from './Rail'
import Medical from './Medical'
import Education from './Education'
import Food from './Food'
import Market from './Market'

const COMPONENTS = {
  smartBus: Bus,
  rail: Rail,
  medical: Medical,
  education: Education,
  food: Food,
  market: Market
}

export default {
  name: 'environment',
  components: {
    VTab
  },
  data () {
    return {
      current: 'smartBus',
      dataValues: {
        smartBus: {
          key: 'smartBus',
          label: '智慧公交站',
          buildings: [{
            icon: 'rail-way',
            status: [{
              label: '地铁站',
              count: 2
            }, {
              label: '运营中',
              count: 2
            }],
            positions: [{
              label: '10号线天潼路站',
              distance: '1.8km'
            }, {
              label: '2号线南京东路站',
              distance: '2.1km'
            }]
          }],
          adMessageTitle: '广告屏状态',
          adMessages: [{
            id: 1,
            name: '1号屏',
            status: '8:00 - 10:00 闲置'
          }, {
            id: 2,
            name: '2号屏',
            status: '9月21日起闲置'
          }],
          messageTitle: '站点实时信息',
          messages: [{
            id: 14,
            icon: 'bus',
            text: '142路',
            status: '还有2站到站',
            schedule: '05:10 - 23:32'
          }, {
            id: 13,
            icon: 'bus',
            text: '78路',
            status: '已到站',
            schedule: '07:00 - 23:30'
          }, {
            id: 12,
            icon: 'bus',
            text: '909路',
            status: '还有3站到站',
            schedule: '06:00 - 21:00'
          }, {
            id: 11,
            icon: 'bus',
            text: '55夜宵线',
            status: '已停运',
            schedule: '23:10 - 03:00'
          }]
        },

        rail: {
          key: 'rail',
          label: '地铁',
          buildings: [{
            icon: 'rail-way',
            status: [{
              label: '地铁站',
              count: 2
            }, {
              label: '运营中',
              count: 2
            }],
            positions: [{
              label: '10号线天潼路站',
              distance: '1.8km'
            }, {
              label: '2号线南京东路站',
              distance: '2.1km'
            }]
          }],
          messageTitle: '站点实时信息',
          messages: [{
            id: 14,
            icon: 'rail-way',
            text: '4号线还有5分钟到达南京路站'
          }, {
            id: 13,
            icon: 'rail-way',
            text: '1号线还有3分钟到达天潼路站'
          }, {
            id: 12,
            icon: 'rail-way',
            text: '167路还有2站到达河南北路宁海路'
          }, {
            id: 11,
            icon: 'rail-way',
            text: '因路口封闭施工，13路云飞路站撤销'
          }]
        },

        medical: {
          key: 'medical',
          label: '医疗',
          buildings: [{
            icon: 'hospital',
            status: [{
              label: '医院',
              count: 4
            }, {
              label: '服务中',
              count: 4
            }]
          }],
          positions: [{
            name: '第二军医大学附...', // 属医院
            distance: '4.6km',
            level: '三级甲等',
            status: '服务中'
          }, {
            name: '徐泾镇社区医院',
            distance: '8km',
            level: '二级甲等',
            status: '服务中'
          }, {
            name: '市人民医院',
            distance: '4.9km',
            level: '三级乙等',
            status: '服务中'
          }, {
            name: '长宁街道社区卫...', // 生中心
            distance: '2.1km',
            level: '一级甲等',
            status: '服务中'
          }]
        },

        education: {
          key: 'education',
          label: '教育',
          buildings: [{
            icon: 'school',
            status: [{
              label: '学校',
              count: 6
            }, {
              label: '服务中',
              count: 6
            }]
          }, {
            icon: 'culture-center',
            status: [{
              label: '文化中心',
              count: 1
            }, {
              label: '服务中',
              count: 1
            }]
          }],
          chart: [{
            name: '幼儿园',
            value: 1,
            color: '#1AA5CF'
          }, {
            name: '小学',
            value: 2,
            color: '#4CCEC7'
          }, {
            name: '中学',
            value: 2,
            color: '#AAE0A1'
          }, {
            name: '大学',
            value: 1,
            color: '#FED138'
          }, {
            name: '文化中心',
            value: 1,
            color: '#EA484D'
          }],
          messageTitle: '教育活动信息',
          messages: [{
            id: 1,
            icon: 'school',
            text: '东华大学向市民开放历史文化课程'
          }, {
            id: 2,
            icon: 'culture-center',
            text: '街道文化中心图书馆延时至21:00'
          }, {
            id: 3,
            icon: 'culture-center',
            text: '文化中心于本周四举办红色电影节'
          }, {
            id: 4,
            icon: 'school',
            text: '长宁附小举办新生迎新活动'
          }]
        },

        food: {
          key: 'food',
          label: '餐饮',
          buildings: [{
            icon: 'resturaturn',
            status: [{
              label: '餐厅',
              count: 176
            }, {
              label: '营业中',
              count: 154
            }]
          }],
          charts: [
            [{
              name: '川菜',
              value: 24,
              color: '#0083F1'
            }, {
              name: '粤菜',
              value: 20,
              color: '#3FF2E8'
            }, {
              name: '淮扬菜',
              value: 18,
              color: '#FD9843'
            }, {
              name: '火锅',
              value: 16,
              color: '#0A589E'
            }, {
              name: '日料',
              value: 12,
              color: '#3EBDE9'
            }, {
              name: '西餐',
              value: 6,
              color: '#FED138'
            }, {
              name: '韩国料理',
              value: 4,
              color: '#F9368A'
            }],
            [{
              name: '人均50元以下',
              value: 24,
              color: '#0083F1'
            }, {
              name: '50-100元',
              value: 40,
              color: '#3EBDE9'
            }, {
              name: '100-200元',
              value: 18,
              color: '#3FF2E8'
            }, {
              name: '200-500元',
              value: 16,
              color: '#FED138'
            }, {
              name: '500元以上',
              value: 16,
              color: '#EA484D'
            }]
          ]
        },

        market: {
          key: 'market',
          label: '超市商场',
          buildings: [{
            icon: 'market',
            status: [{
              label: '商超',
              count: 20
            }, {
              label: '服务中',
              count: 17
            }]
          }],
          chart: [{
            name: '商场',
            value: 2,
            color: '#1685EE'
          }, {
            name: '超市',
            value: 4,
            color: '#3EBDE9'
          }, {
            name: '菜场',
            value: 2,
            color: '#3FF2E8'
          }, {
            name: '便利店',
            value: 12,
            color: '#FED138'
          }],
          messageTitle: '商超活动信息',
          messages: [{
            id: 54,
            icon: 'market',
            text: '联华超市感恩回馈，全场8折'
          }, {
            id: 53,
            icon: 'shop',
            text: '万达广场周四开业酬宾，全场8.8折'
          }, {
            id: 52,
            icon: 'market',
            text: '欧尚新增进口食品专柜'
          }, {
            id: 51,
            icon: 'vagetable',
            text: '街道菜市场缩短营业时间至18:00'
          }]
        }
      }
    }
  },
  computed: {
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
  },
  mounted () {
  },
  methods: {
    onClick (e) {
      this.current = e.key
    }
  }
}
</script>

<style lang="scss" scoped>
.environment {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  .component {
    flex: 1;
  }
}
</style>

