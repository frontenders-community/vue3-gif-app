<script setup>
import GifsList from "./components/GifsList.vue";
import Search from "./components/Search.vue";
import ColorThemeSwitch from "./components/ColorThemeSwitch.vue";

import { onMounted, reactive } from "vue";
import axios from "axios";

const env = import.meta.env;
const state = reactive({
  results: [],
  limit: 16,
  needle: "excited",
  next: '',

});

onMounted(() => {
  searchGifs(state.needle);

  window.onscroll = () => {
    let bottomReached = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;
    if (bottomReached) {
      searchNextGifs(state.needle);
    }
  }
});

function searchGifs(needle) {
  document.documentElement.scrollTop = 0;
  state.needle = needle;
  axios
    .get("https://tenor.googleapis.com/v2/search", {
      params: {
        q: state.needle,
        key: env.VITE_TENOR_API_KEY,
        client_key: env.VITE_TENOR_CLIENT_KEY,
        limit: state.limit,
        pos: state.next
      },
    })
    .then((resp) => {
      state.results = resp.data.results;
      state.next = resp.data.next;
    });
}

function searchNextGifs() {
  axios.get("https://tenor.googleapis.com/v2/search", {
    params: {
      q: state.needle,
      key: env.VITE_TENOR_API_KEY,
      client_key: env.VITE_TENOR_CLIENT_KEY,
      limit: state.limit,
      pos: state.next
    }
  })
    .then((resp) => {
      state.results = [...state.results, ...resp.data.results];
      state.next = resp.data.next;
    })
}
</script>

<template>
  <header>
    <div class="container">
      <!-- Top header -->
      <div class="top">
        <h1>GIFAPP</h1>
        <ColorThemeSwitch/>
      </div>
      <!-- /Top header -->

      <!-- Bottom header -->
      <div class="bottom">
        <Search @start-search="searchGifs" />
      </div>
      <!-- /Bottom header -->
    </div>
  </header>

  <main>
    <div class="container">
      <GifsList :gifs="state.results" />
    </div>
  </main>
</template>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background-color: var(--color-header-background);
  padding-bottom: 2em;
}

header .top {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

main {
  padding-top: 15rem;
}

h1 {
  font-weight: 800;
  font-size: 3.6rem;
}
</style>
