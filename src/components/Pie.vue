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
      chart: null,
      disableLabel: false,
      radius: ['50%', '55%'],
      legend: {
        show: false
      }
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
      const { colors, title, subTitle, data, label } = this.options

      return {
        legend: this.legend,
        title: {
          text: title,
          subtext: subTitle,
          textStyle: {
            fontSize: 16,
            fontWeight: 500,
            color: '#37D1FF'
          },
          subtextStyle: {
            fontSize: 10,
            fontWeight: 300,
            color: '#D7DAED'
          },
          x: 'center',
          top: '40%'
        },
        color: colors || ['#0095F0', '#71DAEE', '#9FE86D', '#C3C3C3'],
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b}: {c} ({d}%)'
        },
        series: [{
          name: label,
          type: 'pie',
          radius: this.radius,
          label: {
            normal: {
              show: !this.disableLabel,
              textStyle: {
                fontSize: 10
              },
              formatter: '{d}%({c})\n\n{b}'
            }
          },
          data
        }]
      }
    }
  }
}
</script>
