<script setup lang="ts">
import constants from '../constants';

defineProps<{
   livedWeeks: number | undefined;
   age: number | undefined;
}>();

const TOTAL_WEEKS = constants.MAX_AGE_YEARS * constants.WEEKS_PER_YEAR;
</script>

<template>
   <div class="text-center mb-16">
      <div v-if="age !== undefined" class="mb-4">{{ age }} years ({{ livedWeeks }} weeks).</div>
      <div class="w-[1050px] mx-auto flex flex-wrap gap-1">
         <WeekSquare
            v-for="(week, weekIndex) in TOTAL_WEEKS"
            :key="weekIndex"
            :is-filled="weekIndex + 1 <= (livedWeeks ?? 0)"
            :is-current="weekIndex + 1 === (livedWeeks ?? 0)"
            :index="weekIndex"
         />
      </div>
      <div class="mt-4">This chart represents a life of 90 years (4680 weeks).</div>
   </div>
</template>