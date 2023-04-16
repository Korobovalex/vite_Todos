<template>
    <header>
        <the-navbar />
    </header>
    <RouterView />
</template>

<script setup>
import { RouterView } from 'vue-router'
import TheNavbar from "./components/TheNavbar.vue";
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500;700&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Rubik', sans-serif;
}
</style>
