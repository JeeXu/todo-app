<template>
  <!-- avatar（头像） -->
  <div class="avatar" :class="{ avatar_selected: !!selected }">
    <div class="avatar_face">
      <!-- <img :src="avatar_imgUrl" alt="头像" /> -->
      <img src="../assets/image/avatar.jpg" alt="头像" />
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
      // avatar_imgUrl: 'https://source.unsplash.com/300x300',
      avatar_name: 'Hello, Jane',
      today: new Date()
      // selected: true
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

<style lang="scss" scoped>
.avatar {
  display: flex;
  padding: 0 40px;
  height: 300px;
  justify-content: flex-end;
  flex-direction: column;
  transition: all 0.5s ease;
}
.avatar_selected {
  transform: translate3d(0 20px, 0);
  opacity: 0;
}
.avatar_face {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  img {
    display: block;
    width: 100%;
    height: 100%;
    // object-fit: cover;
  }
}
.avatar_name {
  margin-top: 32px;
  padding: 0 6px;
  font-size: 32px;
  letter-spacing: 1px;
  font-weight: 300;
}
.avatar_tips {
  margin-top: 16px;
  padding: 0 6px;
  font-size: 13px;
  font-weight: 100;
  opacity: 0.8;
  line-height: 1.6rem;
}
.avatar_date {
  margin-top: 44px;
  margin-bottom: 16px;
  padding: 0 6px;
  font-size: 14px;
}
</style>
