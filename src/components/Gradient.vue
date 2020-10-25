<template>
  <div class="gradient">
    <gradient-color
      v-for="(todo, index) in todos"
      :key="todo.name"
      :colors="todo.colors"
      :active="index <= currentIndex"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import GradientColor from './GradientColor.vue'
export default {
  components: {
    GradientColor
  },
  computed: {
    ...mapState(['todos', 'currentIndex'])
  }
}
</script>

<style lang="scss" scoped>
.gradient {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: -1;
  height: 100vh;
}
</style>
