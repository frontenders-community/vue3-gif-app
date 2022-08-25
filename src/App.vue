<script setup>
import GifsList from "./components/GifsList.vue";
import Search from "./components/Search.vue";

import { onMounted, reactive } from "vue";
import axios from "axios";

const env = import.meta.env;
const state = reactive({
  results: [],
  limit: 8,
  needle: "excited"
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
  <header>
    <Search @start-search="searchGifs" />
  </header>

  <main>
    <div class="container">
      <GifsList :gifs="state.results" />
    </div>
  </main>
</template>

<style scoped>
</style>
