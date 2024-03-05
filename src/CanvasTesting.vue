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
</script>

<style>

html, body {
  margin: 0;
  background: sandybrown;
}
</style>


<template>
  <!--
  <p>window width: {{ windowWidth}}</p>
  <p>window height: {{windowHeight}}</p>
  -->
  <canvas v-bind:width="windowWidth" v-bind:height="windowHeight" style="background-color:#fff; overflow: hidden"></canvas>
</template>
