<script setup lang="ts">
import { RouterLink } from 'vue-router'

defineProps<{ 
  deckNum: number
  title: string
  description: string
  deckSlug: string
}>()

</script>

<template>
  <!-- Use ':to' instead of just 'to' in order to interpret routePath as an expression and not a literal object -->
  <RouterLink :to="deckSlug">
    <div class="flex flex-col pl-4 pr-20 pb-10 pt-4 items-start bg-gray-500 rounded-2xl shadow-xl gap-y-2 transition transformation hover:scale-105 hover:shadow-2xl duration-300 hover:cursor-pointer">
      <h1 class="text-5xl">Deck {{ deckNum }}</h1>
      <h2 class="text-3xl text-blue-300">{{ title }}</h2>
      <p class="text-md">{{ description }}</p>
    </div>
  </RouterLink>
</template>