<script setup lang="ts">
import constants from '../constants';

const emit = defineEmits(['update:birthDate']);

const currentYear = new Date().getFullYear();

const birthMonth = ref<number | undefined>(undefined);
const birthDay = ref<number | undefined>(undefined);
const birthYear = ref<number | undefined>(undefined);

const birthDate = computed(() => {
   if ([birthMonth, birthDay, birthYear].some(({ value }) => value === undefined))
      return undefined;

   return new Date(birthYear.value!, birthMonth.value!, birthDay.value!);
});

function handleAnyInput(): void {
   if (birthDate.value !== undefined)
      emit('update:birthDate', birthDate.value);
}
</script>

<template>
   <form class="flex justify-center items-center gap-2 mt-10">
      <span class="text-2xl mr-2 max-md:text-xl">🗓️</span>
      <select 
         v-model="birthMonth"
         @input="handleAnyInput()"
         class="select select-bordered focus:select-primary placeholder:text-gray-500 max-md:select-sm"
         placeholder="Month"
      >
         <option disabled selected value="undefined">Month</option>
         <option value="0">January</option>
         <option value="1">February</option>
         <option value="2">March</option>
         <option value="3">April</option>
         <option value="4">May</option>
         <option value="5">June</option>
         <option value="6">July</option>
         <option value="7">August</option>
         <option value="8">September</option>
         <option value="9">October</option>
         <option value="10">November</option>
         <option value="11">December</option>
      </select>
      <input
         v-model="birthDay"
         @input="handleAnyInput()"
         type="number"
         class="input input-bordered focus:input-primary placeholder:text-gray-500 max-md:input-sm"
         min="1"
         max="31"
         placeholder="Day"
      />
      <input
         v-model="birthYear"
         @input="handleAnyInput()"
         type="number"
         class="input input-bordered focus:input-primary placeholder:text-gray-500 max-md:input-sm"
         :min="currentYear - constants.MAX_AGE_YEARS"
         :max="currentYear"
         placeholder="Year"
      />
   </form>
</template>