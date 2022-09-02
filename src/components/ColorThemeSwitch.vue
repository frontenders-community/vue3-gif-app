<script setup>
import { onMounted, reactive } from 'vue';

const state = reactive({
    userTheme: "light-theme"
});

onMounted(() => {
    const initUserTheme = getTheme() || getMediaPreference();
    setTheme(initUserTheme);
});

function getMediaPreference() {
    const hasDarkPreference = window.matchMedia("(prefers-color-scheme: dark)").matches;
    if (hasDarkPreference) {
        return "dark-theme";
    } else {
        return "light-theme";
    }
}

function getTheme() {
    return localStorage.getItem("user-theme");
}

function setTheme(theme) {
    localStorage.setItem("user-theme", theme);
    state.userTheme = theme;
    document.documentElement.className = theme;
}

function toggleTheme() {
    console.log('toggle');
    const activeTheme = localStorage.getItem("user-theme");
    if (activeTheme === "light-theme") {
        setTheme("dark-theme");
    } else {
        setTheme("light-theme");
    }
}

</script>

<template>
    <div class="switch-wrapper">
        <input @change="toggleTheme" id="checkbox" type="checkbox" class="switch-checkbox">
        <label for="checkbox" class="switch-label">
            <span>🌙</span>
            <span>☀️</span>
            <div class="switch-toggle" :class="{ 'switch-toggle-checked': state.userTheme === 'dark-theme' }"></div>
        </label>
    </div>
</template>

<style scoped>
.switch-checkbox {
    display: none;
}

.switch-label {
    width: calc(var(--switch-element-size) * 1.2);
    border-radius: var(--switch-element-size);
    border: calc(var(--switch-element-size) * .05) solid var(--color-border);
    padding: calc(var(--switch-element-size) * .25) calc(var(--switch-element-size) * .1);
    font-size: calc(var(--switch-element-size) * .3);
    height: calc(var(--switch-element-size) * .35);

    align-items: center;
    background-color: var(--color-background-soft);
    cursor: pointer;
    display: flex;
    position: relative;
    transition: background .5s ease;
    justify-content: space-between;
    z-index: 1;
}

.switch-toggle {
    position: absolute;
    background-color: var(--color-text);
    border-radius: 50%;
    top: calc(var(--switch-element-size) * .06);
    left: calc(var(--switch-element-size) * .07);
    height: calc(var(--switch-element-size) * .4);
    width: calc(var(--switch-element-size) * .4);
    transform: translateX(0);
    transition: transform .3s ease, background-color .5s ease;
}

.switch-toggle-checked {
    transform: translateX(calc(var(--switch-element-size) * 0.6));
}
</style>