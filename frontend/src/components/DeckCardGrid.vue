<script setup lang="ts">
import DeckCard from './DeckCard.vue'

// TODO: fetch this info from a json database so changes only need to be made in one place.
const deckCards = [
  { deckNum: 1, title: 'Essentials', description: 'Greetings, Politeness, and Basic Phrases', deckSlug: "/deck1-essentials" },
  { deckNum: 2, title: 'Everyday Vocabulary', description: 'Asking and answering everyday questions with confidence', deckSlug: '/deck2-questions-and-responses' },
  { deckNum: 3, title: 'Verbs in Action', description: 'Talk about your home, family, and daily routines', deckSlug: '/deck3-daily-life-and-household-vocab' },
  { deckNum: 4, title: 'Verbs in Action', description: 'Order food, express preferences, and navigate menus with ease', deckSlug: '/deck4-food-drinks-and-ordering' },
]

</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
    <DeckCard v-for="deckCard in deckCards"
      :key="deckCard.deckNum"
      :deckSlug="deckCard.deckSlug"
      :deckNum="deckCard.deckNum"
      :title="deckCard.title"
      :description="deckCard.description"
    />
  </div>
</template>