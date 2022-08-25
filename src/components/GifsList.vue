<script setup>
import GifCard from "./GifCard.vue";

defineProps(["gifs"]);
</script>

<template>
  <div class="gif" v-for="(gif, index) in gifs" :key="index">
    <GifCard :gif="gif" />
  </div>
</template>