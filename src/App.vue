<script setup lang="ts">
import { defineAsyncComponent, ref } from 'vue'

const i = ref(0)
const components = [
  () => import('./components/Comp1.vue'),
  () => import('./components/Comp2.vue'),
  () => import('./components/Comp3.vue')
].map(defineAsyncComponent)
</script>

<template>
  <div>
    <button v-for="item in components.length" @click="i = item - 1">
      {{ item }}
    </button>
  </div>
  <component :is="components[i]" />
</template>
