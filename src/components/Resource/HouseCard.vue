<template>
  <v-pie :options="componentDate"></v-pie>
</template>

<script>

import VPie from '@/components/Charts/Pie'

export default {
  name: 'HouseCard',
  components: {
    VPie
  },
  props: {
    componentDate: {
      type: Object
    }
  }
}
</script>



