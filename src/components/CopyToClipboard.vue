<script setup>
import { ref } from 'vue';
const props = defineProps(['copyText']);
let open = ref(false);

async function copyToClipboard() {
    await navigator.clipboard.writeText(props.copyText);
    open.value = true;
    setTimeout(function () {
        open.value = false;
    }, 5000);
}

</script>

<template>
    <a href="" @click.prevent="copyToClipboard">
        <font-awesome-icon icon="fa-solid fa-link" class="icon" />
    </a>

    <Teleport to="body">
        <Transition>
            <div  v-if="open" class="modal">
                <p>The gif is copied to your clipboard</p>
                <button @click="open = false">Close</button>
            </div>
        </Transition>
    </Teleport>
</template>

<style>
.icon {
    color: white;
    font-size: 2rem;
}

.modal {
    position: fixed;
    z-index: 999;
    top: 0;
    left: 0;
    width: 100%;
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 4em;
    height: 100px;
    background-color: var(--indigo);
    font-size: 1.6rem;
}

button {
    background-color: white;
    border: 1px solid white;
    border-radius: 10px;
    padding: .5em 1em;
    cursor: pointer;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>