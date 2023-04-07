<template>
  <div>
    <ArticleCard />
    <div class="flex flex-col md:flex-row ">
      <todo-item title="买牛奶" description="去超市买一瓶牛奶"></todo-item>
      <todo-item title="学习Vue" description="完成Vue教程"></todo-item>
      <todo-item title="做饭1" description="晚上做顿好吃的"></todo-item>
    </div>
  </div>
  <button @click="show = !show">Toggle Slide + Fade</button>
  <Transition name="slide-fade">
    <p v-if="show">hello</p>
  </Transition>
</template>

<script>
import ArticleCard from "./components/ArticleCard.vue";
import TodoItem from './components/TodoItem.vue'

export default {
  components: {
    ArticleCard,
    TodoItem
  },
  data() {
    return {
      show: true
    }
  },
}
</script>

<style>
/*
  进入和离开动画可以使用不同
  持续时间和速度曲线。
*/
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
