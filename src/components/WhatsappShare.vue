<script setup>
    defineProps(['message']);
</script>

<template>
    <a :href="`https://api.whatsapp.com/send?text=${message}`" target="_blank">
        <font-awesome-icon icon="fa-brands fa-whatsapp" class="icon" />
    </a>
</template>

<style scoped>
.icon {
    color: white;
    font-size: 3rem;
}
</style>