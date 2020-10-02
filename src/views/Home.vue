<template>
  <div class="home">
    <app-bar title="TODO" left="bars" right="search" />
    <avatar />
  </div>
</template>

<script>
import AppBar from '../components/AppBar.vue'
import Avatar from '../components/Avatar.vue'

export default {
  components: {
    AppBar,
    Avatar
  }
}
</script>

<style lang="scss" scoped>
.home {
  height: 100%;
  width: 100%;
  overflow: hidden;
  color: white;
}
</style>
