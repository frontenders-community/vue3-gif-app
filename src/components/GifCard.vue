<script setup>
import WhatsappShare from './WhatsappShare.vue';

defineProps(["gif"]);
</script>

<template>
  <div class="card" v-if="gif.media_formats">
    <img :src="gif.media_formats.tinygif.url" :alt="gif.content_description" />
    <div class="card-overlay">
      <div class="actions">
        <WhatsappShare :message="gif.media_formats.tinygif.url"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  position: relative;
}

.card img {
  width: 100%;
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
  bottom: 0;
  right: 0;
  padding: 1em;
  display: flex;
  align-items: center;
}

.card-overlay .actions span {
  margin-right: 1em;
}

.card:hover .card-overlay {
  display: block;
}
</style>