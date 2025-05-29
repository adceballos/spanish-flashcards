<script setup lang="ts">
import DeckCard from './DeckCard.vue'

</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
      <DeckCard :deckNum="1" title="Basics" description="Greetings and Politeness"/>
      
      <DeckCard :deckNum="2" title="Everyday Vocab" description="People, Places, and Things"/>
  </div>
</template>