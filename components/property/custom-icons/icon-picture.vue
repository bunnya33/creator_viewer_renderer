

<template>
    <svg fill="#000000" :style="{ width: computedSize, height: computedSize }" class="el-icon svg"  viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg"><path d="M13.5 6.73 11 5 7.68 7.53 6 6 2.5 8.49V11h11zm-1.25 3h-8.5v-.59L5.9 7.6l.94.86.77.7.83-.63 2.59-2 1.22.84z"/><ellipse cx="3.3" cy="5.75" rx=".8" ry=".75"/><path d="M14.75 2.5H1.25A1.25 1.25 0 0 0 0 3.75v8.5a1.25 1.25 0 0 0 1.25 1.25h13.5A1.25 1.25 0 0 0 16 12.25v-8.5a1.25 1.25 0 0 0-1.25-1.25zm0 9.75H1.25v-8.5h13.5z"/></svg>
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