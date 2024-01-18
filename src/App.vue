<script setup lang="ts">
import { RouterView } from 'vue-router'
import { onMounted } from "vue";

onMounted(() => {
  const loader = document.getElementById('index-loader')
  if (loader) {
    document.body.removeChild(loader)
  }
  
})
</script>

<template>
  <RouterView />
</template>

