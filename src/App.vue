<script setup>
import { RouterLink, RouterView } from 'vue-router'
import VFooter from './components/VFooter.vue'
</script>

<template>
  <header>
    <div class="wrapper">

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
  <VFooter />
</template>

<style scoped>
</style>
