<template>
  <div class="bg"></div>
  <div class="snow-list">
    <div class="snow-item snow-item-1">
      <div class="snow-bg snow-bg-1"></div>
    </div>
    <div class="snow-item snow-item-2">
      <div class="snow-bg snow-bg-2"></div>
    </div>
    <div class="snow-item snow-item-3">
      <div class="snow-bg snow-bg-3"></div>
    </div>
    <div class="snow-item snow-item-4">
      <div class="snow-bg snow-bg-4"></div>
    </div>
  </div>
  <audio style="visibility: hidden" src="@/assets/audio.mp3"></audio>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'

@Options({
  components: {},
})
export default class Home extends Vue {
  activeIndex: undefined
  onMounted() {
    let i = 1
    const el: any = document.querySelector('.snow-list')
    const bgEl: any = document.querySelector('.bg')
    el.onclick = function () {
      i++
      if (i > 4) i = 1
      bgEl.style.backgroundImage = `url(@/assets/bg${i}.jpeg)`
    }
    document.querySelector('audio')?.play()
  }
  handleSelect() {}
}
</script>

<style scoped>
.bg {
  width: 100%;
  height: 100%;
  background-image: url('../assets/bg1.jpeg');
  background-size: cover;
}
.snow-list {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1;
  height: 100%;
  transition: opacity 1s ease-out;
}
.snow-item {
  width: 100%;
  height: 100%;
  position: absolute;
  background-repeat: repeat;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  top: -100%;
  pointer-events: none;
}
.snow-item-1 {
  animation-duration: 50s;
  animation-name: snow_falling_fore;
}
.snow-item-2 {
  animation-duration: 50s;
  animation-delay: 25s;
  animation-name: snow_falling_fore;
}
.snow-item-3 {
  animation-duration: 70s;
  animation-name: snow_falling_mid; 
  animation-delay: 0s;
  opacity: 0.5;
}
.snow-item-4 {
  animation-duration: 70s;
  animation-delay: 35s;
  animation-name: snow_falling_mid;
  opacity: 0.5;
}
.snow-bg {
  height: 100%;
  background-image: url('../assets/snow.png');
}
.snow-bg-2 {
  background-position: -10px 0;
}
.snow-bg-3 {
  background-position: -50px 0;
}
.snow-bg-4 {
  background-position: -100px -10px;
}
@keyframes snow_falling_fore {
  0% {
    top: -100%;
    opacity: 0;
  }
  1% {
    top: -100%;
    opacity: 1;
  }
  99.8% {
    top: 100%;
    opacity: 1;
  }
  99.9% {
    opacity: 0;
  }
  100% {
    top: -100%;
    opacity: 0;
  }
}
@keyframes snow_falling_mid {
  0% {
    top: -100%;
    opacity: 0;
  }
  1% {
    top: -100%;
    opacity: 1;
  }
  99.8% {
    top: 100%;
    opacity: 1;
  }
  99.9% {
    opacity: 0;
  }
  100% {
    top: -100%;
    opacity: 0;
  }
}
</style>
