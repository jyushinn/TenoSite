<template>
    <div class="flex w-1/2 mx-auto">
      <img :src="imageSrc" @load="onImageLoad" :class="{ 'opacity-0': !imageLoaded, 'animate__animated animate__fadeIn': imageLoaded }">
      <div v-if="!imageLoaded" class="absolute inset-0 flex justify-center items-center bg-gray-100">
      </div>
    </div>
  </template>
  
  <script>
  import "animate.css"
  
  export default {
    data() {
      return {
        imageLoaded: false,
        imageSrc: 'https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Central_Californian_Coastline%2C_Big_Sur_-_May_2013.jpg/2560px-Central_Californian_Coastline%2C_Big_Sur_-_May_2013.jpg'
      }
    },
    methods: {
      onImageLoad() {
        this.imageLoaded = true;
      }
    },
    computed: {
      imageClasses() {
        return {
          'opacity-0': !this.imageLoaded,
          'animate__animated animate__fadeIn': this.imageLoaded
        }
      }
    },
  }
  </script>
  
  <style scoped>

  </style>