<template>
  <div>
    <h2>{{ title }}</h2>
    <p>Full Name: {{ fullName }}</p>

    <input v-model="firstName" placeholder="First Name" />
    <input v-model="lastName" placeholder="Last Name" />

    <button @click="greet">Greet</button>
   
    <p>Greeting Count: {{ greetCount }}</p>
    <p>{{ message }}</p>
  </div>
</template>

<script setup>
import { ref, computed, watch, 
         onBeforeMount, onMounted,
         onBeforeUpdate, onUpdated,
         onBeforeUnmount, onUnmounted } from 'vue'

/* props */
defineProps({
  title: {
    type: String,
    default: 'Vue3 composition API입니다.'
  }
})

/* state */
const firstName  = ref('John')
const lastName   = ref('Doe')
const greetCount = ref(0)
const message    = ref('')

/* computed */
const fullName = computed(() => `${firstName.value} ${lastName.value}`)

/* methods */
function greet() {
  greetCount.value++
  message.value = `Hello, ${fullName.value}!`
}


/* watchers */
watch(greetCount, (newVal, oldVal) => {
  console.log(`Greet count changed from ${oldVal} to ${newVal}`)
  if (newVal >= 3) {
    message.value = "That's enough greetings for now!"
  }
})

/* lifecycle */
onBeforeMount(() => console.log('beforeMount hook'))
onMounted(() => console.log('mounted hook'))
onBeforeUpdate(() => console.log('beforeUpdate hook'))
onUpdated(() => console.log('updated hook'))
onBeforeUnmount(() => console.log('beforeUnmount hook'))
onUnmounted(() => console.log('unmounted hook'))
</script>
