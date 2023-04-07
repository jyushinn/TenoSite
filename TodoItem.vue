<!-- 定义一个 todo-item 组件 -->
<template>
  <div id="overlay" class="overlay" v-if="show" style="display: none;"></div>
  <div class="todo-item p-12" @click="openModal">
    <h3 class="text-red-700 text-2xl">{{ title }}</h3>
    <p class="text-red-400 text-md">{{ description }}</p>
  </div>
</template>

<script>
export default {
  // 使用简略写法定义 props
  props: {
    title: String,
    description: String
  },
  methods: {
    openModal() {
      const overlay = document.getElementById('overlay')
      overlay.style.display = 'block'
      overlay.style.opacity = 0
      setTimeout(() => {
        overlay.style.opacity = 1
      }, 0)
    },
    data() {
    return {
      show: true
    }
  }
  },
}
</script>

<style>
.todo-item:hover,
.todo-item:focus {
  transform: scale(1.2);
  transition: transform 0.3s ease-in-out;
}


/* 将样式限制在当前组件 */
.todo-item:hover body,
.todo-item:focus body {
  background-color: rgba(0, 0, 0, 0.6);
}


.overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(255, 255, 255, 1); /* 白色半透明 */
  z-index: 999; /* 将其置于所有其他元素之上 */
  opacity: 0;
  transition: opacity 0.5s ease-in-out;
}

/* 下面我们会解释这些 class 是做什么的 */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

</style>