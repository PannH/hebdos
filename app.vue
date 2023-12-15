<script setup lang="ts">
useSeoMeta({
   title: 'Hebdos | How many weeks have you been living for?',
   description: 'Discover how many weeks you have been living for and how many weeks you have left to live.'
});

const livedWeeks = ref<number | undefined>(undefined);
const age = ref<number | undefined>(undefined);

function handleBirthDateUpdate(birthDate: Date): void {
   livedWeeks.value = Math.floor((Date.now() - birthDate.getTime()) / (1000 * 60 * 60 * 24 * 7));
   age.value = Math.floor((Date.now() - birthDate.getTime()) / (1000 * 60 * 60 * 24 * 365));
}
</script>

<template>
   <Header />
   <BirthdateForm @update:birth-date="handleBirthDateUpdate" />
   <div class="container mx-auto mt-16">
      <WeeksChart :lived-weeks="livedWeeks" :age="age" />
   </div>
</template>
