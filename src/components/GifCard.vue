<script setup>
defineProps(["gif"]);
</script>

<template>
  <div>
    <img :src="gif.media_formats.tinygif.url" :alt="gif.content_description" />
  </div>
</template>

<style scoped>
  img {
    width: 100%;
  }

</style>