<template>
  <!-- 头部导航栏 -->
  <div class="app-bar">
    <!-- 左边（可自定义图标） -->
    <span class="app-bar_l" @click="$emit('left')">
      <i :class="['fa', `fa-${left}`]"></i>
    </span>
    <!-- 中间 title -->
    <h1>{{ title }}</h1>
    <!-- 右边（可自定义图标） -->
    <span class="app-bar_r" @click="$emit('right')">
      <i :class="['fa', `fa-${right}`]"></i>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    left: {
      type: String,
      default: 'chevron-left'
    },
    right: {
      type: String,
      default: 'ellipsis-v'
    }
  }
}
</script>

<style lang="scss" scoped>
.app-bar {
  display: flex;
  align-items: center;
  height: 44px;
  font-size: 15px;
  z-index: 1;
}
h1 {
  display: flex;
  justify-content: center;
  flex: 1;
  font-size: 15px;
}
span {
  padding: 0 20px;
}
</style>
