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
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 12px;
}

@media (max-width: 1000px) {
  .gifs-grid {
    grid-template-columns: 1fr 1fr 1fr;
  }
}

@media (max-width: 800px) {
  .gifs-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 400px) {
  .gifs-grid {
    grid-template-columns: 1fr;
  }
}

.gif {
  display: inline-block;
  width: 100%;
  height: 100%;
  margin-bottom: 12px;
}
</style>