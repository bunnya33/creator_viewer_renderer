

<template>
    <svg fill="#000000" :style="{ width: computedSize, height: computedSize }" class="el-icon svg"  viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg"><path d="M8 3.63a3.57 3.57 0 0 1 2.49-1.06 2.9 2.9 0 0 1 3 3A3.65 3.65 0 0 1 10.73 9l1 1a4.71 4.71 0 0 0 1.54-1 4.79 4.79 0 0 0 1.42-3.38 4.16 4.16 0 0 0-1.22-3 4.16 4.16 0 0 0-3-1.22 4.79 4.79 0 0 0-3.38 1.34 4.71 4.71 0 0 0-1 1.54l1 1A3.6 3.6 0 0 1 8 3.63zm-6.31-.17 2.59 2.59a4.71 4.71 0 0 0-1.54 1 4.79 4.79 0 0 0-1.42 3.38 4.16 4.16 0 0 0 1.22 3 4.16 4.16 0 0 0 3 1.22 4.79 4.79 0 0 0 3.38-1.42 4.71 4.71 0 0 0 1-1.54l2.74 2.74.89-.88-11-11zM8 12.37a3.57 3.57 0 0 1-2.49 1.06 2.9 2.9 0 0 1-3-3A3.65 3.65 0 0 1 5.26 7L9 10.74a3.57 3.57 0 0 1-1 1.63z"/></svg>
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