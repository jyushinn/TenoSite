<template>
    <div class="relative flex sm:justify-center space-x-4 p-4 bg-blur-lg">
      <!-- 按钮组 -->
      <div class="buttons">
        <button ref="button1" class="button" @click="moveCube(1)">Button 1</button>
        <button ref="button2" class="button" @click="moveCube(2)">Button 2</button>
        <button ref="button3" class="button" @click="moveCube(3)">Button 3</button>
      </div>
      <!-- 方块，使用动态绑定 "style" 属性控制其位置 -->
      <div class="cube left-0 z-0" :style="{ transform: `translateX(${cubePosition}px)` }"></div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  
  export default {
    setup() {
      const animationDuration = 0.5; // 动画持续时间
      const cubePosition = ref(0); // 方块的初始位置
      const buttonPositions = ref([]); // 存储三个按钮的位置信息
      const button1 = ref(null);
      const button2 = ref(null);
      const button3 = ref(null);
  
      onMounted(() => {
        // 在组件挂载后，获取按钮和容器的位置信息，计算出每个按钮相对于容器的左偏移量
        const containerPosition = button1.value.parentElement.parentElement.getBoundingClientRect().left;
        buttonPositions.value = [
          button1.value.getBoundingClientRect().left - containerPosition,
          button2.value.getBoundingClientRect().left - containerPosition,
          button3.value.getBoundingClientRect().left - containerPosition,
        ];
        cubePosition.value = buttonPositions.value[0]; // 将方块的初始位置设置为第一个按钮的位置
      });
  
      function moveCube(buttonIndex) {
        // 移动方块到指定的按钮处
        const buttonPosition = buttonPositions.value[buttonIndex - 1];
        console.log(`Button ${buttonIndex} X Position: ${buttonPosition}`);
        const distanceToMove = buttonPosition - cubePosition.value;
        cubePosition.value = buttonPosition;
        requestAnimationFrame(() => {
          // 使用 CSS 过渡效果实现方块的平滑移动
          document.querySelector('.cube').style.transition = `transform ${animationDuration}s`;
          document.querySelector('.cube').style.transform = `translateX(${buttonPosition}px)`;
        });
      }
  
      return {
        cubePosition,
        buttonPositions,
        button1,
        button2,
        button3,
        moveCube,
      };
    },
  };
  </script>
  
  <style scoped>
  .container {
    @apply relative flex flex-col items-center mt-12;
  }
  
  .buttons {
    @apply flex z-10 ;
  }
  
  .button {
    @apply mr-8 p-2  text-black text-base font-semibold border-none cursor-pointer outline-none;
  }
  
  .cube {
    @apply absolute bottom-0 w-24 h-12  bg-blue-500 transition-transform duration-100 ease-in-out;
  }
  </style>
  