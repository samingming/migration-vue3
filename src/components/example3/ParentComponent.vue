<template>
  <div>
    <ChildComponent
      :message="parentMessage"
      @custom-event="handleEvent"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ChildComponent from './ChildComponent.vue'

// 반응형 데이터
const parentMessage = ref('Hello from parent(vue3 migration)')

// 이벤트 핸들러
function handleEvent(payload) {
  console.log(payload)
}
</script>
