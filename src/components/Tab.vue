<template>
  <ul class="tab">
    <li
      class="tabItem"
      v-for="(item, index) in tabs"
      :key="index"
      :class="{active: current === item.key}"
      @click="onClick(item)"
      :style="{fontSize: `${fontSize}px`}">
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
    },
    fontSize: {
      type: Number,
      default: 12
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
  align-items: center;
  .tabItem {
    color: #2b5274;
    margin-right: 1rem;
    font-weight: 300;
    cursor: pointer;
  }
  .active {
    color: #37d1ff;
  }
}
</style>

