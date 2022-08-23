<script setup>
import { onMounted, reactive } from "vue";
import axios from "axios";

const env = import.meta.env;
const state = reactive({
  results: [],
});

onMounted(() => {
  const limit = 8;
  const needle = "excited";

  axios
    .get("https://tenor.googleapis.com/v2/search", {
      params: {
        q: needle,
        key: env.VITE_TENOR_API_KEY,
        client_key: env.VITE_TENOR_CLIENT_KEY,
        limit: limit,
      },
    })
    .then((resp) => {
      console.log(resp);
      state.results = resp.data.results;
    });
});
</script>

<template>
  <header>Header</header>

  <main>
    <div class="container">
      <div class="gif" v-for="(gif, index) in state.results" :key="index">
        <img :src="gif.media_formats.nanogif.url" :alt="gif.content_description">
      </div>
    </div>
  </main>
</template>

<style scoped>
</style>
