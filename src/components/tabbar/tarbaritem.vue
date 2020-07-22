<template>
  <div class="tab-bar-item" @click="tabbarclick">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-active-icon"></slot>
    </div>
    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "tab-bar-item",
  props: {
    path: String,
    activeColor: {
      type: String,
      default: 'red'
    }
  },
  // data () {
  //   return {
  //     // isActive: true
  //   }
  // },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      // 判断组件是否活跃，活跃状态取 {color: this.activeColor} 不活跃取 {}
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    tabbarclick() {
      this.$router.push(this.path)
    }
  }
}
</script>

<style>
  .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }

  .tab-bar-item img {
    width: 24px;
    margin-top: 3px;
    vertical-align: middle;
  }
</style>
