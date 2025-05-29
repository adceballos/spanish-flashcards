<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import DeckCard from './components/DeckCard.vue'
</script>

<template>
  <DeckCard :deckNum="1" title="Basics"/>
  <HelloWorld msg="Vite + Vue" />
</template>
