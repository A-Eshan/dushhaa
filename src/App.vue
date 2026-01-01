<script setup>
import Navbar from './components/layout/Navbar.vue';
import Footer from './components/layout/Footer.vue';
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <Navbar />
    <RouterView class="grow" />
    <Footer />
  </div>
</template>

<style scoped>

</style>
