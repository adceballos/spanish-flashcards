<script setup lang="ts">
import DeckCard from './DeckCard.vue'
import { ref, onMounted } from 'vue';

type Deck = {
  deckNum: number;
  deckSlug: string;
  title: string;
  description: string;
  cards: Card[];
}

type Card = { 
  front: string;
   back: string;
}

// Reactive object holding all decks loaded from decks.json.
// Using 'ref' ensures reactivity, and 'Record<string, Deck>' provides type safety and autocompletion.
//
// The type 'Record<string, Deck>' is a TypeScript utility type that defines an object
// where:
//   - each key is a string (e.g., "deck1-essentials")
//   - each value is a Deck object (with properties like deckNum, title, description, etc.)
// It's equivalent to writing: { [key: string]: Deck }
//
// This structure mirrors the JSON shape where each deck is stored under a unique key.
//
// We initialize it with an empty object '{}' so the app doesn't break before the data loads.
// Once the fetch is complete, we assign the parsed JSON to this variable.
const decks = ref<Record<string, Deck>>({});

onMounted(async () => {
    try {
      const response = await fetch('/data/decks.json');
      decks.value = await response.json();

    } catch (error) {
      console.error('Failed to load decks:', error);
    }
});
</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
    <DeckCard v-for="deck in decks"
      :key="deck.deckNum"
      :deckSlug="deck.deckSlug"
      :deckNum="deck.deckNum"
      :title="deck.title"
      :description="deck.description"
    />
  </div>
</template>