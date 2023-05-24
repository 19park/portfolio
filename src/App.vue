<script setup>
import {onMounted} from "vue";
import {init} from "./scene.js";

onMounted(init);
</script>

<template>
  <div class="loading">
    <svg class="loading-circle">
      <circle cx="50%" cy="50%" r="25"></circle>
    </svg>
  </div>
  <div class="container">
    <section class="scroll-section" id="scroll-section-0">
      <h1>test..</h1>

      <div class="sticky-elem sticky-elem-canvas">
        <canvas id="video-canvas-0" width="1920" height="1080"></canvas>
      </div>
      <div class="sticky-elem main-message a">
        <p>text</p>
      </div>
    </section>
  </div>
</template>

<style scoped lang="scss">
@import "assets/scss/common";

.container {
  overflow-x: hidden;
}
.scroll-section {
  position: relative;
  padding-top: 50vh;

  /**
    기본적으로 보이지않고, body의 id에 따라서 스크롤이 어떤섹션에 위치했을때 보일지 정한다.
   */
  .sticky-elem {
    display: none;
    position: fixed;
    left: 0;
    width: 100%;

    &.sticky-elem-canvas {
      top: 0;
      height: 100%;

      canvas {
        position: absolute;
        top: 50%;
        left: 50%;
      }
    }
  }
}

#show-scene-0 #scroll-section-0 .sticky-elem {
  display: block;
  will-change: transform, opacity;
}

.loading {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;
  background: white;
  opacity: 0;
  transition: 0.5s;
}
.before-load .container {
  display: none;
}
.before-load .loading {
  opacity: 1;
}
@keyframes loading-spin {
  100% { transform: rotate(360deg); }
}
@keyframes loading-circle-ani {
  0% { stroke-dashoffset: 157; }
  75% { stroke-dashoffset: -147; }
  100% { stroke-dashoffset: -157; }
}
.loading-circle {
  width: 54px;
  height: 54px;
  animation: loading-spin 3s infinite;
}
.loading-circle circle {
  stroke: black;
  stroke-width: 4;
  /* getTotalLength()로 stroke의 길이를 얻어올 수 있음 */
  stroke-dasharray: 157, 157;
  stroke-dashoffset: 0;
  fill: transparent;
  animation: loading-circle-ani 1s infinite;
  /* transition: 1s; */
}
</style>
