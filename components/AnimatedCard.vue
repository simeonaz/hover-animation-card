<script setup lang="ts">
const props = defineProps<{
  label: string;
  description: string;
  icon?: string;
}>();
</script>

<template>
  <CardContainer>
    <div
      class="w-full bg-white p-4 gap-x-8 gap-y-4 rounded-xl sm:p-6 dark:bg-gray-900/50"
    >
      <div class="flex flex-col gap-y-2">
        <div v-if="icon" class="mb-2 pointer-events-none">
          <Icon
            :name="icon"
            class="flex-shrink-0 size-6 text-gray-900 dark:text-white"
          />
        </div>
        <h3
          class="text-[16px] font-bold text-gray-900 truncate dark:text-white"
        >
          {{ props.label || "--" }}
        </h3>
        <p class="text-[15px] text-gray-500 dark:text-gray-500">
          {{ props.description || "--" }}
        </p>
      </div>
    </div>
  </CardContainer>
</template>
