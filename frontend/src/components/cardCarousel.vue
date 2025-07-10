<script setup lang="ts">

defineProps<{ 
  cards: {
    front: string
    back: string
  }[]
}>()
</script>

<template>
  <div class="flex flex-col justify-center gap-8">
    <div
      v-for="(card, index) in cards"
      :key="index"
      class="group w-120 h-84 perspective-distant"
    >
      <div class="relative w-full h-full transition-transform duration-300 transform-3d group-hover:rotate-y-180">
        <div class="absolute w-full h-full backface-hidden bg-gray-500 text-white rounded-2xl shadow-xl flex items-center justify-center flex-col">
          <h1 class="text-5xl">{{ card.front }}</h1>
        </div>

        <div class="absolute w-full h-full backface-hidden rotate-y-180 bg-slate-700 text-white rounded-2xl shadow-xl flex items-center justify-center flex-col">
          <h1 class="text-5xl">{{ card.back }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>