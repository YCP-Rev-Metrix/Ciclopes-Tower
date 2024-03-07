<script>
import { defineComponent } from 'vue';
import { useWindowSize } from '@vueuse/core';
import   Vue  from 'vue';
//import { ref } from 'vue';

//import {createApp} from 'vue';

 export default defineComponent({
   setup() {
     const { width, height } = useWindowSize()
     return {
       windowWidth: width,
       windowHeight: height,
     };
   }
 });



function draw() {
  const canvas = document.getElementById('myCanvas');
  const ctx = canvas.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(0, 0);
  ctx.lineTo(500,500);
  ctx.stroke();
}

window.addEventListener("load", draw);

</script>

<style>

html, body {
  margin: 0;
  background: sandybrown;
}

div {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 0;
}
</style>


<template>
  <!--<div> Height: {{height}} </div>-->
  <canvas v-bind:width="windowWidth" v-bind:height="windowHeight" id="myCanvas" style="background-color:#000;"></canvas>
  <!--<div> Width: {{width}}</div>-->

  <!--<button @click="restrictResize">Click here to resize browser screen</button>-->

</template>
