<!-- hiển thị thanh loading nhỏ -->
<template>
  <div
    :class="{
      'page-loader': true,
      'page-loader--loading': isLoading,
      'page-loader--hidden': !isLoading,
    }"
  >
    <div class="page-loader__bar" />
  </div>
</template>

<script>
import { computed } from 'vue'
import { useUIStore } from '../stores/ui'
import { storeToRefs } from 'pinia'

export default {
  name: 'PageLoader',
  setup() {
    const uiStore = useUIStore()
    const { isLoading } = storeToRefs(uiStore)

    return {
      isLoading,
    }
  },
}
</script>

<style scoped>
.page-loader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10000000;
  pointer-events: none;
  opacity: 0;
  transition:
    width 1350ms ease-in-out,
    opacity 350ms linear,
    left 50ms ease-in-out;
}

.page-loader__bar {
  background-color: var(--bs-primary);
  height: 5px;
  width: 100%;
}

.page-loader--hidden {
  opacity: 0;
}

.page-loader--loading {
  opacity: 1;
  animation: page-loader-loading 2000ms ease-in-out;
  animation-iteration-count: infinite;
}

@keyframes page-loader-loading {
  0% {
    width: 0;
    left: 0;
  }
  50% {
    width: 100%;
    left: 0;
  }
  100% {
    width: 100%;
    left: 100%;
  }
}
</style>
