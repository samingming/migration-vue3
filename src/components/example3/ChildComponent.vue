<template>
  <div>
    <p>{{ props.message }}</p>
    <button @click="emit('custom-event', 'Hello from child')">Send Event</button>
  </div>
</template>

<script setup>
const props = defineProps({ message: String })
const emit = defineEmits(['custom-event'])
</script>
