<script setup lang="ts">
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
