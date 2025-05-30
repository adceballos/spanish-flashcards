<script setup lang="ts">
import DeckCard from './DeckCard.vue'

</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
      <DeckCard :deckNum="1" title="Essentials" description="Greetings, Politeness, and Basic Phrases"/>
      <DeckCard :deckNum="2" title="Everyday Vocabulary" description="People, Places, and Things"/>
      <DeckCard :deckNum="3" title="Verbs in Action" description="Core Spanish Verbs and Daily Activities"/>
  </div>
</template>