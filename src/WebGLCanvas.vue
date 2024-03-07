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
  /** This draws a line from the bottom left corner to the top right corner
  ctx.beginPath()
  ctx.moveTo(width.value, 0);
  ctx.lineTo(0, height.value);
  ctx.stroke();
      **/
  ctx.beginPath();

  const gutter1 = new Path2D();
  gutter1.rect(width.value*0.3, 0, width.value*0.1, height.value);
  const gutter2 = new Path2D();
  gutter2.rect(width.value*0.6, 0, width.value*0.1, height.value);
  const lane = new Path2D();
  lane.rect(width.value*0.3, 0, width.value*0.4, height.value);

  //ctx.arc(width.value*0.48, height.value*0.15, 5, 0, Math.PI*2, true);
  //ctx.moveTo(width.value*0.52, height.value*0.15,);
  //ctx.arc(width.value*0.52, height.value*0.15, 5, 0, Math.PI*2, true);
  ctx.fillStyle = "#e5a06c";
  ctx.fill(lane);
  ctx.fillStyle = "#000000";
  ctx.fill(gutter1);
  ctx.fill(gutter2);

  //  ctx.moveTo(0.5, height.value*0.1);
  //5 pin
  ctx.arc(width.value*0.5, height.value*0.1, 5, 0, Math.PI*2, true);

  //2 pin
  ctx.moveTo(width.value*0.475, height.value*0.15);
  ctx.arc(width.value*0.475, height.value*0.15, 5, 0, Math.PI*2, true);

  //3 pin
  ctx.moveTo(width.value*0.525, height.value*0.15);
  ctx.arc(width.value*0.525, height.value*0.15, 5, 0, Math.PI*2, true);
  //1 pin
  ctx.moveTo(width.value*0.5, height.value*0.2);
  ctx.arc(width.value*0.5, height.value*0.2, 5, 0, Math.PI*2, true);

  //6 pin
  ctx.moveTo(width.value*0.55, height.value*0.1);
  ctx.arc(width.value*0.55, height.value*0.1, 5, 0, Math.PI*2, true);

  //4 pin
  ctx.moveTo(width.value*0.45, height.value*0.1);
  ctx.arc(width.value*0.45, height.value*0.1, 5, 0, Math.PI*2, true);

  //8 pin
  ctx.moveTo(width.value*0.475, height.value*0.05);
  ctx.arc(width.value*0.475, height.value*0.05, 5, 0, Math.PI*2, true);

  //9 pin
  ctx.moveTo(width.value*0.525, height.value*0.05);
  ctx.arc(width.value*0.525, height.value*0.05, 5, 0, Math.PI*2, true);

  //7 pin
  ctx.moveTo(width.value*0.425, height.value*0.05);
  ctx.arc(width.value*0.425, height.value*0.05, 5, 0, Math.PI*2, true);

  //6 pin
  ctx.moveTo(width.value*0.575, height.value*0.05);
  ctx.arc(width.value*0.575, height.value*0.05, 5, 0, Math.PI*2, true);

  ctx.closePath();
  ctx.stroke();

  ctx.fillStyle = "red";
  //create initial triangle
  ctx.moveTo(width.value*0.5, height.value*0.7);
  ctx.lineTo(width.value*0.505, height.value*0.710);
  ctx.lineTo(width.value*0.495, height.value*0.710);
  //cut section out of triangle to make it an arrow
  //IMPORTANT: must go counter-clockwise to make parts of shape dissapear
  //see:https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes

  ctx.moveTo(width.value*0.5, height.value*0.707);
  ctx.lineTo(width.value*0.498, height.value*0.710);
  ctx.lineTo(width.value*0.502, height.value*0.710);
  //calling ctx.fill() fills inside of pin circles
  //if want to avoid this draw arrows before drawing pin
  ctx.fill();

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