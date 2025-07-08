<script setup lang="ts">
import CardCarousel from '../components/cardCarousel.vue';
import { ref, onMounted } from 'vue';

// destructure 'deckSlug' prop passed from the dynamic route defined in 'index.ts' (via 'props: true')
const { deckSlug } = defineProps<{
    deckSlug: string
}>()

type Card = { front: string; back: string }
// Reactive array of card objects, initialized as an empty array. Holds the cards for the selected deck. Using '<Card[]>' to override the default inheritance with our 'Card' complex type. '[]' after card denotes we have an array, and it is of type 'Card'. Reference: https://vuejs.org/guide/typescript/composition-api.html#typing-ref
const cards = ref<Card[]>([])

onMounted(async () => {
    try {
        const response = await fetch('/public/data/decks.json');
        const decks = await response.json();
        cards.value = decks[deckSlug] ?? [];
    } catch (error) {
        console.error('Failed to load decks:', error);
    }
})

</script>

<template>
  <CardCarousel :cards="cards"/>
</template>