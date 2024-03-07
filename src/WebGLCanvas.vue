<script setup>
import { ref, watchEffect, nextTick } from 'vue'
import { useWindowSize } from '@vueuse/core'

const canvas = ref()
const color = ref("red")
const { width, height } = useWindowSize()

function changeColor() {
  color.value = (color.value === "red") ? "blue" : "red"
}

watchEffect(() => {
  if (!canvas.value) return // it's not ready yet
  canvas.value.width = width.value
  canvas.value.height = height.value
  const ctx = canvas.value.getContext('2d')
  ctx.strokeStyle = color.value
  ctx.clearRect(0, 0, width.value, height.value)
  ctx.beginPath()
  ctx.moveTo(width.value, 0);
  ctx.lineTo(0, height.value);
  ctx.stroke();
})
</script>

<template>
  <canvas ref="canvas" id="myCanvas" @click="changeColor" style="background:gray">
  </canvas>
</template>

<style>
#myCanvas {
  display: flex;
}
#app {
  padding: 0;
}
</style>