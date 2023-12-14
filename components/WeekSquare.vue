<script setup lang="ts">
defineProps<{
   isFilled: boolean;
   isCurrent: boolean;
   index: number;
}>();
</script>

<template>
   <div class="tooltip" :data-tip="`#${index + 1} ${isCurrent ? '- Today' : ''}`">
      <div :class="`border rounded w-4 aspect-square ${isCurrent ? 'bg-secondary border-secondary' : isFilled ? 'bg-primary border-primary' : 'border-gray-500'}`"></div>
   </div>
</template>