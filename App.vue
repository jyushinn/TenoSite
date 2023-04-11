<template>
  <div>
    <router-view v-slot="{ Component }">
    <transition name="scale-slide">
      <component :is="Component" />
    </transition>
  </router-view>
    <RouterLink to="/page1">Page 1</RouterLink>
    <RouterLink to="/page2">Page 2</RouterLink>
    <RouterLink to="/page3">Page 3</RouterLink>
    <ArticleCard />
    <div class="flex flex-col md:flex-row ">
      <todo-item title="买牛奶" description="去超市买一瓶牛奶"></todo-item>
      <todo-item title="学习Vue" description="完成Vue教程"></todo-item>
      <todo-item title="做饭1" description="晚上做顿好吃的"></todo-item>
    </div>
    <PictureLoad></PictureLoad>

  </div>

  <button @click="show = !show">Toggle Slide + Fade</button>
  <Transition name="slide-fade">
    <p v-if="show">hello</p>
  </Transition>
  <VideoPlayer></VideoPlayer>
</template>

<script>
import ArticleCard from "./components/ArticleCard.vue";
import TodoItem from './components/TodoItem.vue'
import VideoPlayer from "./components/VideoVue.vue"
import PictureLoad from "./components/PictureLoad.vue"

export default {
  components: {
    ArticleCard,
    TodoItem,
    VideoPlayer,
    PictureLoad
  },
  data() {
    return {
      show: true
    }
  },
}
</script>

<style>
.scale-slide-enter-active,
.scale-slide-leave-active {
  position: absolute;
  transition: all 0.85s ease;
}
.scale-slide-enter-from {
  left: -100%;
}
.scale-slide-enter-to {
  left: 0%;
}
.scale-slide-leave-from {
  transform: scale(1);
}
.scale-slide-leave-to {
  transform: scale(0.8);
}
</style>
