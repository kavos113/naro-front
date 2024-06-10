<script setup lang="ts">
import ItemList from './ItemList.vue'

defineProps<{
  msg: string
}>()
</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <ItemList />
  </div>
</template>

<style scoped>

</style>
