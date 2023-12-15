<script setup lang="ts">
import constants from '../constants';

const props = defineProps<{
   isFilled: boolean;
   isCurrent: boolean;
   index: number;
}>();

const age = Math.floor((props.index + 1) / constants.WEEKS_PER_YEAR);
</script>

<template>
   <div class="tooltip" :data-tip="`#${index + 1} (${age} year old) ${isCurrent ? '- Today' : ''}`">
      <div :class="`border rounded w-4 aspect-square ${isCurrent ? 'bg-secondary border-secondary' : isFilled ? 'bg-primary border-primary' : 'border-gray-500'}`"></div>
   </div>
</template>