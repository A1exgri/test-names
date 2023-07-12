<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Footer from '@/components/Footer.vue'
</script>

<template>
    <div class="container">

        <RouterView />

        <Footer />
    </div>
</template>

<style>
body {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
#app {
    background: rgba(244, 245, 245, 1);
    font-family: Lato;
    min-height: 100Vh;
}
.container {
    margin: 0 auto;
    width: 100%;
    max-width: 375px;
}
</style>
