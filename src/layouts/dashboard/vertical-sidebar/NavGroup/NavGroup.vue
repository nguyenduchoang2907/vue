<script setup lang="js">
const props = defineProps({ item: Object })
</script>

<template>
  <li class="pc-item pc-caption">
    <label>{{ props.item?.header }}</label>
  </li>
</template>

<style>
.pc-caption {
  font-size: 12px;
  color: #6c757d;
  padding: 12px 16px 4px;
  text-transform: uppercase;
  font-weight: 600;
  letter-spacing: 0.5px;
  display: block;
}
.pc-caption label {
  display: block;
}
</style>
