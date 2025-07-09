<script setup lang="ts">
import { useDark, useToggle } from "@vueuse/core";

const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>

<template>
  <button
    @click="toggleDark()"
    class="cursor-pointer focus:outline-none"
    :class="isDark ? 'text-white' : 'text-gray-600'"
  >
    <Icon
      :name="isDark ? 'mdi:white-balance-sunny' : 'mdi:moon-waning-crescent'"
      class="size-6"
    />
  </button>
</template>
