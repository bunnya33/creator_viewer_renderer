

<template>
    <svg fill="#000000" :style="{ width: computedSize, height: computedSize }" class="el-icon svg"  viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg"><path d="M14.12 4 8.62.85a1.28 1.28 0 0 0-1.24 0L1.88 4a1.25 1.25 0 0 0-.63 1.09V11a1.25 1.25 0 0 0 .63 1l5.5 3.11a1.28 1.28 0 0 0 1.24 0l5.5-3.11a1.25 1.25 0 0 0 .63-1V5.05A1.25 1.25 0 0 0 14.12 4zm-6.74 9.71-2.13-1.2v-5.3l2.13 1.16zM8 7.29 5.92 6.15l4.81-2.67 2.09 1.18zm0-5.35 1.46.82-4.84 2.69-1.44-.79zM2.5 5.71l1.5.82v5.27L2.5 11zm6.12 8V8.37l4.88-2.66V11z"/></svg>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  size?: number | string  // 可传 16 / '1em' / '24px'
}>()

const computedSize = computed(() => {
  return typeof props.size === 'number' ? `${props.size}px` : props.size || '1em'
})
</script>

<style>

</style>