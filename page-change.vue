<template>
  <nav class="flex sm:justify-center space-x-4 p-4 bg-blur-lg">
    <router-link v-for="page in pages" :key="page.title" :to="page.url" class="rounded-lg px-3 py-2 text-slate-700 font-medium hover:bg-slate-100 hover:text-slate-500 active:bg-violet-200 active:scale-125">
      {{ page.title }}
    </router-link>
  </nav>
  <router-view v-slot="{ Component }">
    <transition name='slide'>
      <Component :is="Component" />
    </transition>
  </router-view>
</template>

<script>
export default {
  data() {
    return {
      pages: [
        { title: "Page 1", url: "/page1" },
        { title: "Page 2", url: "/page2" },
        { title: "Page 3", url: "/page3" },
      ],
    };
  },
};
</script>

<style scoped>
.wrapper {
  width: 100%;
  min-height: 100vh;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.75s cubic-bezier(0.25, 0.8, 0.25, 1.05);
}

.slide-enter-to {
  position: absolute;
  right: 0;
}

.slide-enter-from {
  position: absolute;
  right: -100%;
}

.slide-leave-to {
  position: absolute;
  left: -100%;
}

.slide-leave-from {
  position: absolute;
  left: 0;
}
</style>
