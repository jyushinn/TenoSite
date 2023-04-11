<template>
  <div class="flex w-1/2 mx-auto">
    <video-player
      class="video-player vjs-big-play-centered"
      src="https://vjs.zencdn.net/v/oceans.mp4"
      poster="https://vjs.zencdn.net/v/oceans.png"
      crossorigin="anonymous"
      playsinline
      controls
      :volume="0.6"        
      :height="320"            
      @mounted="handleMounted"
      @ready="handleEvent($event)"
      @play="handleEvent($event)"
      @pause="handleEvent($event)"
      @ended="handleEvent($event)"
      @loadeddata="handleEvent($event)"
      @waiting="handleEvent($event)"
      @playing="handleEvent($event)"
      @canplay="handleEvent($event)"
      @canplaythrough="handleEvent($event)"
      @timeupdate="handleEvent(player?.currentTime())"
    />
  </div>
  </template>
   
  <script>
    import { defineComponent, shallowRef } from 'vue'
    import { VideoPlayer } from '@videojs-player/vue'
    import 'video.js/dist/video-js.css'
   
    export default {
      name: 'vue-basic-player-example',
      title: 'Basic player (Vue)',
      components: {
        VideoPlayer
      },
      setup() {
        //可打印出当前所触发的事件
        const handleEvent = (log) => {
          console.log('Basic player event', log)
        }
   
        return { handleEvent }
      }
    }
  </script>
   
  <style scoped>
    .video-player {
      background-color: black;
      width: 100%;
    }
  </style>