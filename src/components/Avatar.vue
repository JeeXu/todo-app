<template>
  <!-- avatar（头像） -->
  <div class="avatar" :class="{ avatar_selected: !!selected }">
    <div class="avatar_face">
      <img :src="avatar_imgUrl" alt="头像" />
    </div>
    <!-- 姓名 -->
    <h2 class="avatar_name">{{ avatar_name }}</h2>
    <!-- todo 提示 -->
    <p class="avatar_tips">
      Look like feed good.<br />You have {{ todayTasks.length }} tasks to do
      today
    </p>
    <p class="avatar_date">TODAY : {{ today | dateString }}</p>
  </div>
</template>

<script>
import { mapState, mapGetters } from 'vuex'

export default {
  data() {
    return {
      avatar_imgUrl: 'https://source.unsplash.com/300x300',
      avatar_name: 'Hello, Jane',
      today: new Date()
    }
  },
  computed: {
    ...mapState(['selected']),
    ...mapGetters(['todayTasks'])
  },
  filters: {
    dateString(val) {
      return val
        .toDateString()
        .toUpperCase()
        .replace(/(\s\d{4})$/, ', $1')
    }
  }
}
</script>

<style lang="scss" scoped></style>
