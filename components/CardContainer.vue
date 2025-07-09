<script setup lang="ts">
const dom = ref<HTMLElement | null>(null); // DOM element reference
const cursorXPosition = ref(-350); // cursor X Position (initially out of screen)
const cursorYPosition = ref(-350); // cursor Y Position (initially out of screen)

function mouseMoveGradient(e: MouseEvent) {
  if (dom.value) {
    const rect = dom.value.getBoundingClientRect();
    const diffX = e.clientX - rect.x; // Relative X position within the element
    const diffY = e.clientY - rect.y; // Relative Y position within the element
    cursorXPosition.value = diffX;
    cursorYPosition.value = diffY;
  }
}

onMounted(() => {
  document.addEventListener("mousemove", mouseMoveGradient, false);
});

onUnmounted(() => {
  document.removeEventListener("mousemove", mouseMoveGradient, false);
});
</script>

<template>
  <div
    ref="dom"
    class="cover relative isolate rounded-xl background-gradient ring-1 ring-gray-200 dark:ring-gray-800 before:hidden before:lg:block before:absolute before:-inset-[2px] before:h-[calc(100%+4px)] before:w-[calc(100%+4px)] before:z-[-1] before:rounded-[13px] flex-1 flex flex-col shadow transition-shadow duration-200"
    :style="{ '--x': cursorXPosition + 'px', '--y': cursorYPosition + 'px' }"
  >
    <div
      class="flex-1 flex flex-col overflow-hidden rounded-xl divide-y divide-gray-200 dark:divide-gray-800 bg-white dark:bg-gray-900 hover:bg-opacity-90 dark:hover:bg-opacity-90 transition-[background-opacity] dark:bg-gradient-to-b from-gray-700/50 to-gray-900/50 cursor-pointer"
    >
      <slot />
    </div>
  </div>
</template>

<style scoped>
.cover:before {
  background: radial-gradient(
    250px circle at var(--x) var(--y),
    #40c371 0,
    transparent 100%
  );
}
</style>
