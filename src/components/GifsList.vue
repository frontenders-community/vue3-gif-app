<script setup>
import { ref, nextTick } from 'vue';
import GifCard from "./GifCard.vue";

const props = defineProps(["gifs"]);


</script>

<template>
  <div class="gifs-grid">
    <div class="gif" v-for="(gif, index) in gifs" :key="index">
      <GifCard :gif="gif" />
    </div>
  </div>
</template>

<style scoped>
.gifs-grid {
  line-height: 0;
  column-count: 4;
  column-gap: 12px;
}

@media (max-width: 1200px) {
  .gifs-grid {
    -moz-column-count: 4;
    -webkit-column-count: 4;
    column-count: 4;
  }
}

@media (max-width: 1000px) {
  .gifs-grid {
    -moz-column-count: 3;
    -webkit-column-count: 3;
    column-count: 3;
  }
}

@media (max-width: 800px) {
  .gifs-grid {
    -moz-column-count: 2;
    -webkit-column-count: 2;
    column-count: 2;
  }
}

@media (max-width: 400px) {
  .gifs-grid {
    -moz-column-count: 1;
    -webkit-column-count: 1;
    column-count: 1;
  }
}

.gif {
  display: inline-block;
  width: 100%;
  height: auto;
  margin-bottom: 12px;
}
</style>