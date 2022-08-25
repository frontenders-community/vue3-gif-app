<script setup>
    import { reactive } from "vue";

    const state = reactive({
        needle: ""
    }) 

    const emit = defineEmits(['start-search']);

    function startSearch() {
        emit('start-search', state.needle);
    }

</script>

<template>
    <div>
        <input @keyup.enter="startSearch" v-model="state.needle" type="text">
        <button @click="startSearch">Search</button>
    </div>
</template>