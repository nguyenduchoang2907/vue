<script setup lang="js">
import { RouterLink } from 'vue-router'
</script>

<template>
  <div class="header-container">
    <RouterLink to="/" class="brand-link" aria-label="logo">
      <img src="/favicon.svg" class="logo-image" alt="logo" />
    </RouterLink>
  </div>
</template>

<style scoped>
.header-container {
  display: flex;
  align-items: center;
  height: 60px;
  padding: 0 16px;
}

.brand-link {
  color: #0d6efd;
  text-decoration: none;
  display: flex;
  align-items: center;
}

.logo-image {
  height: auto;
  max-height: 40px;
}
</style>
