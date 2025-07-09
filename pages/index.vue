<script setup>
import { cardsData } from "~/cards.data";
useHead({
  title: "Card Border Animation",
  description:
    "Card Border Animation made with Nuxt & TailwindCSS by Siméon Azogbonon",
});

const cards = cardsData;
</script>

<template>
  <div class="flex items-center justify-center py-8 sm:py-16">
    <section class="py-8 px-4 sm:px-20">
      <div class="grid grid-cols-1 gap-6 sm:grid-cols-2 xl:grid-cols-4">
        <AnimatedCard
          v-for="(card, i) in cards"
          :key="i"
          :label="card.label"
          :description="card.description"
          :icon="card.icon"
        />
      </div>
    </section>
  </div>
</template>

<style scoped>
.text-primary {
  color: rgb(0, 220, 140);
}
</style>
