<template>
  <div class="bus" :label="label">
    <div class="img">
      <v-image :src="src"></v-image>
    </div>
    <div class="positions">
      <v-address :position="position"></v-address>
    </div>
    <div class="messages">
      <v-message :messageTitle="messageTitle" :messages="messages"></v-message>
    </div>
    <div class="adstatuses">
      <v-ad-message :adMessageTitle="adMessageTitle" :adMessages="adMessages"></v-ad-message>
    </div>
  </div>
</template>

<script>

import VImage from './_components/Image'
import VAddress from './_components/Address'
import VMessage from './_components/Message'
import VAdMessage from './_components/AdMessage'

export default {
  name: 'Bus',
  components: {
    VImage,
    VAddress,
    VMessage,
    VAdMessage
  },
  props: {
    componentDate: {
      type: Object
    }
  },
  data () {
    return {
      src: require('../../assets/bus.svg'),
      position: {
        name: '天潼路河南路',
        distance: '1.6km',
        level: '天潼路河南路路口',
        status: '服务中'
      }
    }
  },
  computed: {
    label () {
      return this.componentDate.label
    },
    messageTitle () {
      return this.componentDate.messageTitle
    },
    messages () {
      return this.componentDate.messages
    },
    adMessageTitle () {
      return this.componentDate.adMessageTitle
    },
    adMessages () {
      return this.componentDate.adMessages
    }
  },
  mounted () {
    console.log(this.componentDate)
  }
}
</script>


<style lang="scss" scoped>
.bus {
  height: 100%;
  display: flex;
  .img {
    flex: .7;
  }
  .positions, .messages, .adstatuses {
    // display: flex;
    // justify-content: center;
    // align-items: center;
  }
  .positions {
    flex: 1.4;
    border-right: 1px solid #25376a;
  }
  .messages {
    flex: 2;
    border-right: 1px solid #25376a;
  }
  .adstatuses {
    flex: .7;
    padding-left: 1rem;
    padding-right: 0;
  }
}
</style>

