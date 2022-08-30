<script setup>
import { ref, nextTick } from 'vue';
import GifCard from "./GifCard.vue";

const props = defineProps(["gifs"]);
const gifsRefs = ref([]);
const gridHeight = [0, 0, 0, 0];

function calculateTransform(gifIndex) {
  const columnWidth = 1040 * 0.25 - 16;
  // Left position calculation
  const column = gifIndex % 4;
  let leftPosition = column * 1040 * 0.25;
  if (column !== 0) {
    leftPosition += 8;
  }
  // Top position
  let topPosition = gridHeight[column];
  if (gifsRefs.value.length > 0) {
    console.log(gifsRefs.value[gifIndex].clientHeight);
    gridHeight[column] += gifsRefs.value[gifIndex].clientHeight;
  }

  return `translate3d(${leftPosition}px, ${topPosition}px, 0)`

}
</script>

<template>
  <div class="gifs-grid">
    <div class="gif" v-for="(gif, index) in gifs" :key="index" :style="{ transform: calculateTransform(index) }"
      ref="gifsRefs">
      <GifCard :gif="gif" />
    </div>
  </div>
</template>

<style scoped>
.gifs-grid {
  position: relative;
}

.gif {
  position: absolute;
  width: calc(100% / 4 - 16px);
}
</style>