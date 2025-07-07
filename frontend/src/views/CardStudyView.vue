<script setup lang="ts">
import CardCarousel from '../components/cardCarousel.vue';

// destructure 'deckSlug' prop passed from the dynamic route defined in 'index.ts' (via 'props: true')
const { deckSlug } = defineProps<{
    deckSlug: string
}>()

const decks: Record<string, { front: string; back: string }[]> = {
    "deck1-essentials": [
        { front: "Hola", back: "Hello" },
        { front: "Adios", back: "Goodbye" },
    ],
    "deck2-everyday-vocabulary": [
        { front: "Casa", back: "House" },
        { front: "Comida", back: "Food" },
    ],
}

const cards = decks[deckSlug] ?? [];
</script>

<template>
  <CardCarousel :cards="cards"/>
</template>