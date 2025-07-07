<script setup lang="ts">
import DeckCard from './DeckCard.vue'

const deckCards = [
  { deckNum: 1, title: 'Essentials', description: 'Greetings, Politeness, and Basic Phrases', deckSlug: "/deck1-essentials" },
  { deckNum: 2, title: 'Everyday Vocabulary', description: 'People, Places, and Things', deckSlug: '/deck2-everyday-vocabulary' },
  { deckNum: 3, title: 'Verbs in Action', description: 'Core Spanish Verbs and Daily Activities', deckSlug: '/deck3-verbs-in-action' },
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