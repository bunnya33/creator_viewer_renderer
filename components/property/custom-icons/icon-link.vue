

<template>
    <svg fill="#000000" :style="{ width: computedSize, height: computedSize }" class="el-icon svg"  viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg"><path d="M8 6.1a.31.31 0 0 0-.45.32 2.47 2.47 0 0 0 .51 1.22l.15.13A3 3 0 0 1 9.08 10a3.63 3.63 0 0 1-3.55 3.44 3 3 0 0 1-2.11-.85 3 3 0 0 1-.85-2.22A3.55 3.55 0 0 1 3.63 8a3.66 3.66 0 0 1 1.5-.91A5.19 5.19 0 0 1 5 6v-.16a4.84 4.84 0 0 0-2.31 1.3 4.5 4.5 0 0 0-.2 6.37 4.16 4.16 0 0 0 3 1.22 4.79 4.79 0 0 0 3.38-1.42 4.52 4.52 0 0 0 .21-6.38A4.16 4.16 0 0 0 8 6.1z"/><path d="M13.46 2.54a4.16 4.16 0 0 0-3-1.22 4.79 4.79 0 0 0-3.37 1.42 4.52 4.52 0 0 0-.21 6.38A4.21 4.21 0 0 0 8 9.9a.31.31 0 0 0 .45-.31 2.41 2.41 0 0 0-.52-1.23l-.15-.13A3 3 0 0 1 6.92 6a3.63 3.63 0 0 1 3.55-3.44 3 3 0 0 1 2.11.85 3 3 0 0 1 .85 2.22A3.55 3.55 0 0 1 12.37 8a3.66 3.66 0 0 1-1.5.91 5.19 5.19 0 0 1 .13 1.14v.16a4.84 4.84 0 0 0 2.31-1.3 4.5 4.5 0 0 0 .15-6.37z"/></svg>
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