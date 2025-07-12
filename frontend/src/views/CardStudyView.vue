<script setup lang="ts">
import CardCarousel from '../components/cardCarousel.vue';
import { ref, onMounted } from 'vue';

// destructure 'deckSlug' prop passed from the dynamic route defined in 'index.ts' (via 'props: true')
const { deckSlug } = defineProps<{
    deckSlug: string;
}>();

type Card = {
  front: string;
  back: string;
};

type Deck = {
  cards: Card[];
};

const cards = ref<Card[]>([]);

onMounted(async () => {
  try {
    const response = await fetch('/data/decks.json');
    const data: Record<string, Deck> = await response.json();

    const deck = data[deckSlug];
    cards.value = deck?.cards ?? [];
  } catch (error) {
    console.error('Failed to load deck:', error);
  }
});
</script>

<template>
  <CardCarousel :cards="cards"/>
</template>