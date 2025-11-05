<template>
  <div>
    <ChildComponent1 />
  </div>
</template>

<script setup>
import { provide } from 'vue'
import ChildComponent1 from '@/components/example4/ChildComponent1.vue'

// 부모에서 하위 트리에 값 제공
provide('sharedMessage', 'Vue-3 migration 예제실습')
</script>
