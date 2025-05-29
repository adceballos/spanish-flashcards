<script setup lang="ts">

defineProps<{ 
  deckNum: number
  title: string
  description: string
  // routePath: string
}>()

</script>

<template>
  <div class="flex flex-col pl-4 pr-24 pb-8 pt-4 items-start bg-gray-500 rounded-2xl shadow-xl gap-y-2">
    <h1 class="text-5xl">Deck {{ deckNum }}</h1>
    <h2 class="text-3xl text-blue-300">{{ title }}</h2>
    <p class="text-xl">{{ description }}</p>
  </div>
</template>