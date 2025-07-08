<script setup lang="ts">
import { RouterLink } from 'vue-router';
import { ref } from 'vue';
import { useParallax } from '@vueuse/core';

const container = ref(null);
const hasInteracted = ref(false);

const { tilt, roll } = useParallax(container);
const SCALE_CONSTANT = -30;

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
    <div ref="container" @mouseenter="hasInteracted = true" class="flex flex-col pl-4 pr-20 pb-10 pt-4 items-start bg-gray-500 rounded-2xl shadow-xl gap-y-2 hover:cursor-pointer" :style="{
      transform: hasInteracted
      ? `rotateX(${roll * SCALE_CONSTANT}deg) rotateY(${tilt * SCALE_CONSTANT}deg)`
      : 'rotateX(0deg) rotateY(0deg)'
    }">
      <h1 class="text-5xl">Deck {{ deckNum }}</h1>
      <h2 class="text-3xl text-blue-300">{{ title }}</h2>
      <p class="text-md">{{ description }}</p>
    </div>
  </RouterLink>
</template>