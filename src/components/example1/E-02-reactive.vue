<template>
  <div>{{ fullName }}</div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'

const firstName = ref("Saim")
const lastName = ref("Jeong")

const fullName = computed(() => `${firstName.value} ${lastName.value}`)

onMounted(() => {
  setTimeout(() => {
    firstName.value = "JSI"
  }, 2000)
})
</script>
