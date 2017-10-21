<template>
  <div class="rail">Rail</div>
</template>

<script>
export default {
  name: 'Rail',
  props: {
    componentDate: {
      type: Object
    }
  },
  data () {
    return {

    }
  },
  mounted () {
    console.log(this.componentDate)
  }
}
</script>
