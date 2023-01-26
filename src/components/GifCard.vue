<script setup>
import WhatsappShare from './WhatsappShare.vue';
import CopyToClipboard from './CopyToClipboard.vue';

defineProps(["gif"]);
</script>

<template>
  <div class="card" v-if="gif.media_formats">
    <img :src="gif.media_formats.tinygif.url" :alt="gif.content_description" />
    <div class="card-overlay">
      <div class="actions">
        <CopyToClipboard :copyText="gif.media_formats.tinygif.url"/>
        <WhatsappShare :message="gif.media_formats.tinygif.url"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  position: relative;
  height: 100%;
}

.card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.card-overlay {
  display: none;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: var(--overlay-background);
  color: white;
}

.card-overlay .actions {
  position: absolute;
  inset: 0;
  padding: 1em;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
}

.card-overlay .actions span {
  margin-right: 1em;
}

.card:hover .card-overlay {
  display: block;
}


</style>