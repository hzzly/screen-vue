<template>
  <div :class="className" :id="id" :style="{height:height,width:width}"></div>
</template>

<script>
import echarts from 'echarts'
export default {
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    id: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '100%'
    },
    options: {
      type: Object
    }
  },
  data () {
    return {
      chart: null
    }
  },
  mounted () {
    this.chart = echarts.init(document.getElementById(this.id))
    const option = this.getOption()
    this.chart.setOption(option)
  },
  beforeDestroy () {
    if (!this.chart) {
      return
    }
    this.chart.dispose()
    this.chart = null
  },
  methods: {
    getOption () {
      const { colors, data } = this.options

      return {
        color: colors || [
          'rgba(255, 40, 39, 1)',
          'rgba(126, 211, 33, 1)',
          'rgba(254, 216, 74, 0)',
          'rgba(252, 49, 138, 0)'
        ],
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            label: {
              backgroundColor: '#6a7985'
            }
          }
        },
        grid: {
          top: '15%',
          left: '3%',
          right: '12%',
          bottom: '15%',
          containLabel: true
        },
        legend: {
          data: data.map(e => ({ name: e.name, icon: 'circle' })),
          // left: '50%',
          bottom: 0,
          textStyle: {
            color: '#fff'
          }
        },
        xAxis: [
          {
            type: 'category',
            boundaryGap: false,
            data: Array.apply(null, Array(24)).map((e, i) => i < 10 ? `0${i}:00` : `${i}:00`),
            axisLabel: {
              textStyle: {
                fontSize: 10,
                color: '#CCC'
              }
            },
            axisTick: {
              show: false
            },
            axisLine: {
              show: false
            },
            name: '时间',
            nameLocation: 'end',
            nameTextStyle: {
              color: '#CCC',
              fontSize: '10px'
            }
          }
        ],
        yAxis: [
          {
            type: 'value',
            interval: 100,
            splitLine: {
              show: true,
              lineStyle: {
                color: 'rgba(61, 62, 95, 1)',
                type: 'dashed'
              }
            },
            axisLabel: {
              textStyle: {
                fontSize: 10,
                color: '#CCC'
              }
            },
            axisTick: {
              show: false
            },
            axisLine: {
              show: false
            },
            name: '数量           ',
            nameLocation: 'end',
            nameGap: 15,
            nameTextStyle: {
              color: '#CCC',
              align: 'left',
              fontSize: '10px'
            }
          }
        ],
        series: data.map(e => ({
          smooth: true,
          showSymbol: false,
          type: 'line',
          ...e
        }))
        // [
        //   {
        //     smooth: true,
        //     showSymbol: false,
        //     name: '已占用',
        //     type: 'line',
        //     data: [120, 132, 101, 134, 90, 230, 210]
        //   },
        //   {
        //     smooth: true,
        //     showSymbol: false,
        //     name: '可使用',
        //     type: 'line',
        //     data: [220, 182, 191, 234, 290, 330, 310]
        //   },
        // ]
      }
    }
  }
}
</script>
