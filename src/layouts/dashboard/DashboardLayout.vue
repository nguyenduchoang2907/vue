<script setup lang="js">
import { RouterView } from 'vue-router'
import VerticalSidebar from './vertical-sidebar/VerticalSidebar.vue'
import VerticalHeader from './vertical-header/VerticalHeader.vue'
import Footer from './FooterBlock.vue'
import LoaderWrapper from '../LoaderWrapper.vue'
</script>

<template>
  <VerticalSidebar />
  <VerticalHeader />
  <div class="pc-container">
    <div class="pc-content">
      <LoaderWrapper />
      <RouterView />
    </div>
  </div>
  <Footer />
</template>

<style>
.pc-container {
  padding-left: 260px;
  padding-top: 70px;
  min-height: 100vh;
  background-color: #f8f9fa;
}

.pc-content {
  padding: 24px;
}

@media (max-width: 768px) {
  .pc-container {
    padding-left: 0;
  }
}
</style>
