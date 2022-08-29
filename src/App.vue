<script setup>
import GifsList from "./components/GifsList.vue";
import Search from "./components/Search.vue";

import { onMounted, reactive } from "vue";
import axios from "axios";

const env = import.meta.env;
const state = reactive({
  results: [],
  limit: 8,
  needle: "excited",
});

onMounted(() => {
  searchGifs(state.needle);
});

function searchGifs(needle) {
  state.needle = needle;
  axios
    .get("https://tenor.googleapis.com/v2/search", {
      params: {
        q: state.needle,
        key: env.VITE_TENOR_API_KEY,
        client_key: env.VITE_TENOR_CLIENT_KEY,
        limit: state.limit,
      },
    })
    .then((resp) => {
      console.log(resp);
      state.results = resp.data.results;
    });
}
</script>

<template>
  <div class="container">
    <header>
      <h1>GIFAPP</h1>
      <Search @start-search="searchGifs" />
    </header>

    <main>
      <GifsList :gifs="state.results" />
    </main>
  </div>
</template>

<style scoped>
header {
  margin-bottom: 2rem;
}

h1 {
  font-weight: 800;
  font-size: 3.6rem;
}
</style>
