<script setup lang="ts">
import { ref, computed } from 'vue'
import { useRoute } from 'vue-router'

const props = defineProps({
  item: Object
})

const route = useRoute()
const isOpen = ref(false)

// Check if the menu item is active or if any of its children are active
const isActive = computed(() => {
  return props.item && (route.path === props.item.route || (props.item.children && props.item.children.some((child: { route: string }) => child.route === route.path)))
})

// Automatically open if any child is active
const isExpanded = computed(() => {
  return isActive.value || isOpen.value
})

// Toggle submenu on click if the item has children
const toggleMenu = () => {
  if (props.item && props.item.children) {
    isOpen.value = !isOpen.value
  }
}
</script>

<template>
  <li>
    <div
      @click="toggleMenu"
      :class="{
        'bg-[#72d169] text-white': isActive, // Active state
        'text-gray-700 hover:bg-gray-300': !isActive // Default state
      }"
      class="flex items-center justify-between gap-3 rounded-md px-4 py-2 font-medium transition duration-300 cursor-pointer"
    >
      <div class="flex items-center gap-3">
        <span v-if="item && item.icon" v-html="item.icon"></span>
        {{ item?.label }}
      </div>
      <!-- Show dropdown arrow if item has children -->
      <span v-if="item && item.children">==</span>
    </div>

    <!-- Display children if available -->
    <ul v-if="item && item.children && isExpanded" class="ml-6 mt-1 space-y-1">
      <li v-for="child in item?.children" :key="child.route">
        <router-link
          :to="child.route"
          class="flex items-center gap-3 rounded-md px-4 py-2 font-medium transition duration-300"
          :class="{
            'bg-[#72d169] text-white': route.path === child.route, // Highlight active child
            'text-gray-600 hover:bg-gray-200': route.path !== child.route // Default child styling
          }"
        >
          {{ child.label }}
        </router-link>
      </li>
    </ul>
  </li>
</template>
