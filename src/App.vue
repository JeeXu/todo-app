<template>
  <div id="app" class="container" style="">
    <transition>
      <router-view />
    </transition>
  </div>
</template>

<style lang="scss">
// @import url('https://cdn.bootcdn.net/ajax/libs/font-awesome/5.9.0/css/fontawesome.css');
@import url('https://cdn.bootcdn.net/ajax/libs/font-awesome/4.7.0/css/font-awesome.css');
@import url('https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/4.5.3/css/bootstrap-grid.min.css');

body {
  user-select: none;
  background-color: rgba(221, 221, 221, 0.5);
}

#app {
  position: relative;
  height: 100vh;
  max-width: 540px;
  padding: 0;
}
</style>
