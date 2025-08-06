<script setup lang="js">
import { ref, computed, watch, nextTick } from 'vue'
import { useRoute } from 'vue-router'
import NavItem from '../NavItem/NavItem.vue'

const props = defineProps({ item: Object, level: Number })
const route = useRoute()
const expandedItem = ref(null)
const submenu = ref(null)

const isAnyChildActive = (items) => {
  return items?.some(
    (sub) =>
      sub.to?.toLowerCase() === route.path.toLowerCase() ||
      (sub.children && isAnyChildActive(sub.children))
  )
}

const isActive = computed(() => {
  return (
    props.item?.to?.toLowerCase() === route.path.toLowerCase() ||
    isAnyChildActive(props.item?.children || [])
  )
})

watch(
  () => route.path,
  async () => {
    expandedItem.value = isActive.value ? props.item?.title : null
    await nextTick()
    if (submenu.value && isActive.value) {
      submenu.value.style.display = 'block'
    }
  },
  { immediate: true }
)

const toggleMenu = async () => {
  const isExpanded = expandedItem.value === props.item?.title
  expandedItem.value = isExpanded ? null : props.item?.title
  await nextTick()
  if (submenu.value) {
    if (expandedItem.value === props.item?.title) {
      slideDown(submenu.value)
    } else {
      slideUp(submenu.value)
    }
  }
}

const slideDown = async (el) => {
  await nextTick()
  el.style.removeProperty('padding')
  el.style.display = 'block'
  el.style.overflow = 'hidden'
  const height = el.scrollHeight + 'px'
  el.style.height = height
  setTimeout(() => {
    el.style.overflow = 'visible'
    el.style.height = '100%'
  }, 301)
}

const slideUp = async (el) => {
  el.style.height = el.scrollHeight + 'px'
  await nextTick()
  el.style.overflow = 'hidden'
  el.style.display = 'block'
  el.style.height = '0px'
  el.style.padding = '0px'
  setTimeout(() => {}, 301)
}
</script>

<template>
  <li
    :class="[
      'pc-item',
      'pc-hasmenu',
      { 'pc-trigger': expandedItem === item?.title, active: expandedItem === item?.title }
    ]"
  >
    <a href="javascript:void(0)" class="pc-link" @click.prevent="toggleMenu">
      <div class="pc-micon" v-if="props.item?.icon">
        <i :class="['ph ' + props.item?.icon]"></i>
      </div>
      <span class="pc-mtext">{{ props.item?.title }}</span>
      <span class="pc-arrow"><i class="ti ti-chevron-right"></i></span>
      <span class="pc-badge" v-if="props.item?.chip">{{ props.item?.chip }}</span>
    </a>
    <ul ref="submenu" v-if="props.item?.children" class="pc-submenu">
      <template v-for="(subitem, i) in props.item?.children" :key="i">
        <NavCollapse v-if="subitem.children" :item="subitem" :level="(level ?? 0) + 1" />
        <NavItem v-else :item="subitem" :level="(level ?? 0) + 1" />
      </template>
    </ul>
  </li>
</template>

<style scoped>
.pc-submenu {
  transition: all 0.3s ease-in-out;
}
</style>
