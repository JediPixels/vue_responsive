<script setup lang="ts">
import Responsive from './components/responsive.vue';
</script>

<template>
  <h1>R E S P O N S I V E</h1>
  <h1>🎯</h1>
  
  <Responsive />
</template>

<style scoped>
h1 {
  color: orange;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
