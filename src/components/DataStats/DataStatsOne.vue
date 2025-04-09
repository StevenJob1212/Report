<script setup lang="ts">
import { ref } from 'vue'

const cardItems = ref([
  {
    title: 'Sales',
    total: 150,
    trend: 'up',
    bgColor: 'bg-[#00DFFC]' // Bright cyan
  },
  {
    title: 'Revenue',
    total: 532,
    trend: 'up',
    bgColor: 'bg-[#FF8C42]' // Orange
  },
  {
    title: 'New Customers',
    total: 450,
    trend: 'down',
    bgColor: 'bg-[#C77DFF]' // Purple
  },
  {
    title: 'Stock',
    total: 143,
    trend: 'down',
    bgColor: 'bg-[#7D8CA3]' // Blue-gray
  }
])
</script>

<template>
  <!-- Now each item is in a separate row -->
  <div class="flex flex-col gap-4">
    <div
      v-for="(item, index) in cardItems"
      :key="index"
      :class="`${item.bgColor} relative rounded-lg px-6 py-5 text-white overflow-hidden shadow-md`"
    >
      <!-- Decorative background circles -->
      <div class="absolute top-0 right-0 w-24 h-24 bg-white/15 rounded-full -translate-y-1/2 translate-x-1/2"></div>
      <div class="absolute top-5 right-10 w-28 h-28 bg-white/10 rounded-full"></div>
      <div class="absolute bottom-0 left-0 w-32 h-32 bg-white/10 rounded-full translate-y-1/2 -translate-x-1/2"></div>

      <!-- Card content -->
      <div class="relative z-10 flex flex-row justify-between h-full w-full">
        <div class="text-base font-semibold">{{ item.title }}</div>
        <div class="mt-3 flex items-center text-2xl font-bold space-x-1">
          <span>{{ item.total }}</span>
          <span v-if="item.trend === 'up'" class="text-white">↑</span>
          <span v-else class="text-white">↓</span>
        </div>
      </div>
    </div>
  </div>
</template>
