<template>
  <div>이것은 vue3모습입니다, {{ message }}</div>
</template>

<script setup>
import { ref } from 'vue'

const message = ref('Vue3!')
</script>

<style scoped>
div {
  color: blue;
}
</style>
