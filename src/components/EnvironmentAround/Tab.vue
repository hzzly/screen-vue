<template>
  <ul class="tab">
    <li
      class="tabItem"
      v-for="(item, index) in tabs"
      :key="index"
      :class="{active: current === item.key}"
      @click="onClick(item)">
      {{item.label}}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'tab',
  props: {
    tabs: {
      type: Array,
      default: []
    },
    current: {
      type: String
    }
  },
  methods: {
    onClick (e) {
      console.log(e.key)
      this.$emit('onClick', e)
    }
  }
}
</script>


<style lang="scss" scoped>
.tab {
  display: flex;
  .tabItem {
    font-size: 18px;
    color: #2b5274;
    margin-right: 1rem;
    margin-bottom: 0.5rem;
    font-weight: 300;
    cursor: pointer;
  }
  .active {
    color: #37d1ff;
  }
}
</style>

