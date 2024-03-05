<script>
import { defineComponent } from 'vue';
import { useWindowSize } from '@vueuse/core';

export default defineComponent({
  setup() {
    const { width, height } = useWindowSize()
    return {
      windowWidth: width,
      windowHeight: height,
    };
  }
});


const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

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
  <div>
  <canvas v-bind:width="windowWidth" v-bind:height="windowHeight" id="myCanvas" style="background-color:#fff;"></canvas>
  </div>
</template>
