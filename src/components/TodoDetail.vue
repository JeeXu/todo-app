<template>
  <transition name="show" @enter="handleEnter" @leave="handleLeave">
    <div class="todo-detail" v-if="selected">
      <app-bar @left="unselectTodo" />
      <todo :todo="selected.todo" />
    </div>
  </transition>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
import AppBar from './AppBar.vue'
import Todo from './Todo.vue'
export default {
  name: 'TodoDetail',
  components: {
    AppBar,
    Todo
  },
  computed: {
    ...mapState(['selected', 'unselect'])
  },
  methods: {
    ...mapMutations(['unselectTodo']),
    handleEnter(el) {
      Object.assign(el.style, {
        top: `${this.selected.rect.top}px`,
        left: `${this.selected.rect.left}px`,
        width: `${this.selected.rect.width}px`,
        height: `${this.selected.rect.height}px`
      })
      setTimeout(() => {
        Object.assign(el.style, {
          top: 0,
          left: 0,
          width: `${this.selected.rect.appWidth}px`,
          height: `${this.selected.rect.appHeight}px`
        })
      }, 0)
    },
    handleLeave(el) {
      Object.assign(el.style, {
        top: 0,
        left: 0,
        width: `${this.unselect.rect.appWidth}px`,
        height: `${this.unselect.rect.appHeight}px`
      })

      setTimeout(() => {
        Object.assign(el.style, {
          top: `${this.unselect.rect.top}px`,
          left: `${this.unselect.rect.left}px`,
          width: `${this.unselect.rect.width}px`,
          height: `${this.unselect.rect.height}px`
        })
      })
    }
  }
}
</script>

<style lang="scss">
// 此处不加 scoped   让此处css代码能够覆盖 todo 组件
.todo-detail {
  position: absolute;
  flex-direction: column;
  border-radius: 0;
  background-color: #fff;
  color: #666;
  will-change: top, left, width, height;
  .todo {
    height: 100%;
    overflow: auto;
    margin: 0;
    margin-top: -44px;
    padding: 0 20px;
    box-shadow: none;
  }
  .todo_head,
  .todo_body {
    transform: translate3d(0, 88px, 0);
  }
  .todo_menu {
    opacity: 0;
  }
  .todo_tasks {
    overflow: auto;
    opacity: 1;
    transform: scale3d(1, 1, 1);
  }
  .app-bar {
    position: static;
    background-color: rgba(255, 255, 255, 0.85);
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
.show-enter-to,
.show-leave {
  border-radius: 0;
  .todo {
    padding: 0 20px;
  }
  .todo_head,
  .todo_body {
    transform: translate3d(0, 88px, 0);
  }
  .todo_menu {
    opacity: 0;
  }
  .todo_tasks {
    opacity: 1;
    transform: scale3d(1, 1, 1);
  }
  .app-bar {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
.show-leave-to,
.show-enter {
  border-radius: 0;
  .todo {
    padding: 0;
  }
  .todo_head {
    transform: translate3d(0, 0, 0);
  }
  .todo_body {
    transform: translate3d(0, 189px, 0);
  }
  .todo_menu {
    opacity: 1;
  }
  .todo_tasks {
    opacity: 0;
    transform: scale3d(1, 0, 1);
  }
  .app-bar {
    opacity: 0;
    transform: translate3d(0, -100%, 0);
  }
}
.show-enter-active,
.show-leave-active {
  transition: all 0.5s ease;
  .todo,
  .todo_head,
  .todo_body,
  .todo_menu,
  .todo_tasks,
  .app-bar {
    transition: all 0.5s ease;
  }
}
</style>
