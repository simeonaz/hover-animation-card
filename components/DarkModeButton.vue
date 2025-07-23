<script setup lang="ts">
const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>

<template>
  <button
    @click="toggleDark()"
    type="button"
    class="cursor-pointer flex-shrink-0 rounded-md gap-x-1.5 p-1.5 text-gray-700 dark:text-gray-200 hover:text-gray-900 dark:hover:text-white hover:bg-gray-200 dark:hover:bg-gray-700 inline-flex items-center"
  >
    <Icon
      :name="isDark ? 'mdi:white-balance-sunny' : 'mdi:moon-waning-crescent'"
      class="size-6"
    />
  </button>
</template>
