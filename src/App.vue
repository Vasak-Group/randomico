<script setup>
import { RouterView } from 'vue-router'
import VFooter from './components/VFooter.vue'
import NavBar from './components/NavBar.vue';
</script>

<template>
  <NavBar />

  <RouterView />

  <VFooter />
</template>

<style scoped>
</style>
