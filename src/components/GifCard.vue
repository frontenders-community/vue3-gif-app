<script setup>
defineProps(["gif"]);
</script>

<template>
  <div>
    <img :src="gif.media_formats.nanogif.url" :alt="gif.content_description" />
  </div>
</template>