<script setup lang="ts">
import Cartas from './Cartas.vue'

//TODO: make reusable button component
</script>

<template>
  <div class="w-full max-w-7xl mx-auto min-h-screen flex items-center justify-center px-12">

    <div class="flex flex-col gap-y-12 text-wrap w-full">
      <h1 class="text-7xl text-blue-300 text-left">
        Flip Into Language Fluency!
      </h1>
      <h2 class="text-3xl text-left">
        All the words and phrases you need. <br>
        No fluff, just flashcards.
      </h2>
      <button class="bg-slate-700 px-6 py-3 rounded-full hover:bg-slate-600 hover:scale-105 transition duration-200 w-fit">
        Get Started
      </button>
    </div>

    <div class="mr-9">
      <Cartas />
    </div>
  </div>
</template>