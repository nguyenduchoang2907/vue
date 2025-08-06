<script setup lang="js">
import { shallowRef, ref, onMounted, onBeforeUnmount } from 'vue'
import { BImg } from 'bootstrap-vue-next'

// third party
import SimpleBar from 'simplebar-vue'

// files
import sidebarItems from './sidebarItem'

// components
import Logo from '../logo/LogoMain.vue'
import NavGroup from './NavGroup/NavGroup.vue'
import NavItem from './NavItem/NavItem.vue'
import NavCollapse from './NavCollapse/NavCollapse.vue'

// responsive flag
const isSmallScreen = ref(window.innerWidth <= 1024)

const updateScreenSize = () => {
  isSmallScreen.value = window.innerWidth <= 1024
}

onMounted(() => {
  updateScreenSize()
  window.addEventListener('resize', updateScreenSize)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateScreenSize)
})

const sidebarMenu = shallowRef(sidebarItems)
</script>

<template>
  <!-- [ Sidebar Menu ] start -->
  <nav class="pc-sidebar">
    <div class="navbar-wrapper">
      <Logo />
      <div class="navbar-content">
        <SimpleBar style="height: calc(100vh - 90px)">
          <ul class="pc-navbar">
            <template v-for="(item, i) in sidebarMenu" :key="i">
              <NavGroup v-if="item.header" :item="item" :key="item.title" />
              <NavCollapse v-else-if="item.children" :item="item" :level="0" />
              <NavItem v-else :item="item" />
            </template>
          </ul>
          <div class="card pc-user-card my-3 bg-white bg-opacity-10">
            <!-- Optional: User profile card or other content -->
          </div>
        </SimpleBar>
      </div>
    </div>
  </nav>
  <!-- [ Sidebar Menu ] end -->
</template>

<style>
.pc-sidebar {
  position: fixed;
  top: 0;
  left: 0;
  width: 260px;
  height: 100vh;
  background-color: #0d6efd;
  color: #fff;
  display: flex;
  flex-direction: column;
  z-index: 1030;
}

.navbar-wrapper {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.navbar-content {
  flex: 1;
  overflow: hidden;
}

.pc-navbar {
  list-style: none;
  padding: 0;
  margin: 0;
}

.pc-navbar > * {
  margin-bottom: 0.25rem;
}

.pc-user-card {
  margin: 1rem;
  padding: 1rem;
  border-radius: 8px;
  background-color: rgba(255, 255, 255, 0.1);
  color: #fff;
}

@media (max-width: 1024px) {
  .pc-sidebar {
    width: 100%;
    height: auto;
    position: relative;
  }
}
</style>
