<script setup lang="ts">

defineProps<{ 
  deckNum: number
  title: string
  // routePath: string
}>()

</script>

<template>
  <div class="flex flex-col px-4 pb-12 pt-4 items-start bg-gray-500 rounded-2xl shadow-xl m-6 gap-y-2">
    <h1 class="text-5xl">Deck {{ deckNum }}</h1>
    <h2 class="text-3xl text-blue-300">{{ title }}</h2>
    <p class="text-xl">Greetings and Politeness</p>
  </div>
</template>