<template>
  <v-line :options="componentDate"></v-line>
</template>

<script>

import VLine from '@/components/Charts/Line'

export default {
  name: 'TrafficCard',
  components: {
    VLine
  },
  props: {
    componentDate: {
      type: Object
    }
  }
}
</script>





