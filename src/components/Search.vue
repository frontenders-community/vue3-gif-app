<script setup>
import { reactive } from "vue";

const state = reactive({
  needle: "",
});

const emit = defineEmits(["start-search"]);

function startSearch() {
  if (state.needle.trim()) {
    emit("start-search", state.needle);
  }
}
</script>

<template>
  <div class="input-wrapper">
    <input @keyup.enter="startSearch" v-model="state.needle" type="text" placeholder="Search all GIFs by keyword"/>
    <button @click="startSearch">
      <font-awesome-icon icon="fa-solid fa-magnifying-glass" class="icon" />
    </button>
  </div>
</template>

<style scoped>
.input-wrapper {
  display: flex;
}
input {
  flex-grow: 1;
  padding-left: 1.2em;
  padding-right: 1.2em;
  font-size: 1.8rem;
  letter-spacing: 1px;
  border-radius: 0.6rem 0 0 0.6rem;
  border: 0;
}

@keyframes gradient-loop {
    0% {
        background-position: 0 0;
    }
    100% {
        background-position: 100% 0;
    }
}

button {
  color: var(--color-text);
  font-size: 2.4rem;
  width: 50px;
  height: 50px;
  border-radius: 0 0.6rem 0.6rem 0;
  border: 0;
  background-image: linear-gradient(
    45deg,
    rgb(153, 51, 255),
    rgb(255, 102, 102),
    rgb(153, 51, 255)
  );
  background-size: 500%;
  animation: gradient-loop 2s infinite linear;
  padding: 0;
}

button:hover {
  cursor: pointer;
}

button .icon {
  transform: rotateY(180deg);
}
</style>