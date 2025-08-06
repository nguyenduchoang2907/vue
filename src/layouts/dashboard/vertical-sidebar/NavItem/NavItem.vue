<script setup lang="js">
import { computed, onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'

const props = defineProps({
  item: Object,
  level: Number
})
const emit = defineEmits(['childActive'])

const route = useRoute()

const isActive = computed(() => {
  return route.path.toLowerCase() === props.item?.to?.toLowerCase()
})

onMounted(() => {
  if (isActive.value) {
    emit('childActive', props.item?.title)
  }
})

const relativeURL = ref('')
onMounted(() => {
  try {
    relativeURL.value = import.meta.env.BASE_URL
  } catch (error) {
    console.error('Error url not found:', error)
  }
})

const linkTo = computed(() => {
  if (props.item?.getURL && props.item?.type === 'external') {
    return '/'
  } else if (props.item?.getURL) {
    return `${relativeURL.value}${props.item.to}`
  } else {
    return props.item?.to
  }
})

const handleClick = (e) => {
  document.querySelector('.pc-sidebar')?.classList.remove('mob-sidebar-active')
  document.querySelector('.pc-sidebar .pc-menu-overlay')?.remove()
  if (props.item?.getURL && props.item?.type === 'external') {
    e.preventDefault()
    window.open(props.item?.to, '_blank')
  }
}
</script>

<template>
  <li :class="['sidebar-item', { active: isActive }]">
    <a
      :href="linkTo"
      class="sidebar-link"
      @click="handleClick"
    >
      <i :class="['sidebar-icon', props.item.icon]"></i>
      <span class="sidebar-title">{{ props.item.title }}</span>
    </a>
  </li>
</template>

<style>
.sidebar-item {
  list-style: none;
}

.sidebar-link {
  display: flex;
  align-items: center;
  padding: 10px 16px;
  text-decoration: none;
  color: #333;
  transition: background-color 0.3s;
}

.sidebar-link:hover {
  background-color: #f1f1f1;
}

.sidebar-icon {
  margin-right: 10px;
}

.sidebar-title {
  font-size: 14px;
}

.sidebar-item.active > .sidebar-link {
  background-color: #e0e0e0;
  font-weight: bold;
}
</style>
