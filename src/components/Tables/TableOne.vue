<script setup lang="ts">
import { ref } from 'vue'

import BrandOne from '@/assets/images/brand/photo_2024-12-02_20-52-46.jpg'
import BrandTwo from '@/assets/images/brand/photo_2024-12-02_20-52-57.jpg'
import BrandThree from '@/assets/images/brand/photo_2024-12-02_20-53-11.jpg'
import BrandFour from '@/assets/images/brand/photo_2024-12-02_20-53-16.jpg'
import BrandFive from '@/assets/images/brand/photo_2024-12-02_20-52-57.jpg'
import { RouterLink } from 'vue-router'

const brandData = ref([
  {
    logo: BrandOne,
    name: 'Pheaktra',
    visitors: "Web Development",
    revenues: 'office',
    time: "10:00AM",
    conversion: "onTime"
  },
  {
    logo: BrandTwo,
    name: 'Labubu',
    visitors: "Designer",
    revenues: 'office',
    time: "10:25AM",
    conversion: "Late"
  },
  {
    logo: BrandThree,
    name: 'Jame',
    visitors: "IT Support",
    revenues: 'Remote',
    time: "7:15AM",
    conversion: "onTime"
  },
  {
    logo: BrandFour,
    name: 'jame3',
    visitors: 1.5,
    revenues: 'office',
    time: "7:00PM",
    conversion: "onTime"
  },
  {
    logo: BrandFive,
    name: 'Facebook',
    visitors: 3.5,
    revenues: 'Remote',
    time: "8:00AM",
    conversion: "Late"
  }
])
</script>

<template>
  <div
    class="rounded-sm border border-stroke bg-white px-5 pt-6 pb-2.5 shadow-default dark:border-strokedark dark:bg-boxdark sm:px-7.5 xl:pb-1"
  >
  <div class=" flex flex-row-reverse">
    <RouterLink to="/forms/form-elements" class=" bg-blue-600 w-40 h-10 rounded-2xl flex flex-col justify-center text-center font-medium text-whiten">
      
      Add Employees
    </RouterLink>
  </div>

    <h4 class="mb-6 text-xl font-semibold text-black dark:text-white">Attendance Overview</h4>
    

    <div class="flex flex-col">
      <div class="grid grid-cols-3 rounded-sm bg-gray-2 dark:bg-meta-4 sm:grid-cols-5">
        <div class="p-2 xl:p-5">
          <h5 class="text-sm font-medium uppercase xsm:text-base">Employees Name</h5>
        </div>
        <div class="p-2.5 text-center xl:p-5">
          <h5 class="text-sm font-medium uppercase xsm:text-base">Designation</h5>
        </div>
        <div class="p-2.5 text-center xl:p-5">
          <h5 class="text-sm font-medium uppercase xsm:text-base">Type</h5>
        </div>
        <div class="hidden p-2.5 text-center sm:block xl:p-5">
          <h5 class="text-sm font-medium uppercase xsm:text-base">Check In Time</h5>
        </div>
        <div class="hidden p-2.5 text-center sm:block xl:p-5">
          <h5 class="text-sm font-medium uppercase xsm:text-base">Status</h5>
        </div>
      </div>

      <div
        v-for="(brand, key) in brandData"
        :key="key"
        :class="`grid grid-cols-3 sm:grid-cols-5 ${
          key === brandData.length - 1 ? '' : 'border-b border-stroke dark:border-strokedark'
        }`"
      >
        <div class="flex items-center gap-3 p-2.5 xl:p-5">
          <div class="flex-shrink-0">
            <img :src="brand.logo" alt="Brand" class=" w-15 rounded-3xl"/>
          </div>
          <p class="hidden text-black dark:text-white sm:block">{{ brand.name }}</p>
        </div>

        <div class="flex items-center justify-center p-2.5 xl:p-5">
          <p class="text-black dark:text-white">{{ brand.visitors }}</p>
        </div>

        <div class="flex items-center justify-center p-2.5 xl:p-5">
          <p class="text-meta-3">{{ brand.revenues }}</p>
        </div>

        <div class="hidden items-center justify-center p-2.5 sm:flex xl:p-5">
          <p class="text-black dark:text-white">{{ brand.time }}</p>
        </div>

        <div class="hidden items-center justify-center p-2.5 sm:flex xl:p-5">
          <p class="inline-flex rounded-full bg-opacity-10 py-1 px-3 text-sm font-medium"
          :class="{
            'bg-success text-success':brand.conversion === 'onTime',
            'bg-danger text-danger':brand.conversion === 'Late'
          }"
          >{{ brand.conversion }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
