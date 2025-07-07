<script setup lang="ts">

defineProps<{ 
  cards: {
    front: string
    back: string
  }[]
}>()
</script>

<template>
    <div v-for="card in cards" class="flex flex-col py-30 px-50 items-center bg-gray-500 rounded-2xl shadow-xl gap-y-2">
        <h1 class="text-5xl">{{ card.front }}</h1>
    </div>
</template>