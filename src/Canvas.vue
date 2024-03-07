<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'


const canvas = document.getElementById('myCanvas');
//const ctx = canvas.getContext('2d');
function draw() {
  ctx.strokeStyle = "red";
  ctx.beginPath();
  ctx.moveTo(0, 0);
  ctx.lineTo(100, 100);
  ctx.lineTo(200, 100);
  ctx.stroke();
}

//window.addEventListener("load", draw);
</script>

<style>
div {
  position:fixed;
  inset:0;
  height:fit-content;
  width:fit-content;
  margin:auto;
}
#myCanvas {
  border-style: solid;
  border-color: silver;
  border-width: 10px 20px;
  background: sandybrown;
  width: 100%;
  height: 100%;
  display: block;
}
</style>


<script>
</script>

<template>
  <div>
  <canvas id="myCanvas"></canvas>
  </div>
</template>