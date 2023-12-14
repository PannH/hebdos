<script setup lang="ts">
import constants from '../constants';

const currentYear = new Date().getFullYear();

const birthMonth = ref<number | undefined>(undefined);
const birthDay = ref<number | undefined>(undefined);
const birthYear = ref<number | undefined>(undefined);
</script>

<template>
   <form class="flex justify-center items-center gap-2 mt-10">
      <span class="text-2xl mr-2">🗓️</span>
      <select v-model="birthMonth" class="select select-bordered focus:select-primary placeholder:text-gray-500" placeholder="Month" >
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
         type="number"
         class="input input-bordered focus:input-primary placeholder:text-gray-500"
         min="1"
         max="31"
         placeholder="Day"
      />
      <input
         v-model="birthYear"
         type="number"
         class="input input-bordered focus:input-primary placeholder:text-gray-500"
         :min="currentYear - constants.MAX_AGE_YEARS"
         :max="currentYear"
         placeholder="Year"
      />
   </form>
</template>