<script setup>
    import { reactive } from "vue";

    const state = reactive({
        needle: ""
    }) 

    const emit = defineEmits(['start-search']);

    function startSearch() {
        if(state.needle.trim()) {
            emit('start-search', state.needle);
        }
    }

</script>

<template>
    <div class="input-wrapper">
        <input @keyup.enter="startSearch" v-model="state.needle" type="text">
        <button @click="startSearch">
            <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
        </button>
    </div>
</template>

<style scoped>
.input-wrapper {
    display: flex;
}
input {
    flex-grow: 1;    
    padding-left: 20px;
    padding-right: 20px;
    font-size: 1.2rem;
}

button {
    width: 50px;
    height: 50px;
}
</style>