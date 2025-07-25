<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import Card from './Card.vue';
import { ArrowLeftCircleIcon, ArrowRightCircleIcon } from '@heroicons/vue/20/solid';

// Destructure the 'cards' prop directly from defineProps()
// This extracts the 'cards' array from the props object, so we can use 'cards' directly in this script.
// Equivalent to:
// const props = defineProps<...>();
// const cards = props.cards;
const { cards } = defineProps<{
  cards: {
    front: string;
    back: string;
  }[];
}>();

const activeIndex = ref(0);

const nextCard = () => {
  if (activeIndex.value < cards.length - 1) {
    activeIndex.value++;
  }
};

const prevCard = () => {
  if (activeIndex.value > 0) {
    activeIndex.value--;
  }
};

// Define a handler function for keydown events
// Checks if the user pressed the left or right arrow key and triggers the corresponding navigation function
const handleKey = (e: KeyboardEvent) => {
  if (e.key === "ArrowLeft") {
    prevCard();
  } else if (e.key === "ArrowRight") {
    nextCard();
  }
};

// Register the keydown listener when the component is mounted
// Ensures that keyboard navigation works as soon as the component is visible
onMounted(() => {
  window.addEventListener("keydown", handleKey)
});

// Clean up the listener when the component is unmounted
// Prevents memory leaks and accidental navigation after the component is gone
onUnmounted(() => {
  window.removeEventListener("keydown", handleKey)
});
</script>

<template>
  <!-- 'min-h-[calc(100vh-4rem)]' sets height to be height of screen - height of header component. Used to remove scroll on page. -->
  <div class="flex flex-col items-center justify-center min-h-[calc(100vh-4rem)]">
    <div v-if="cards.length > 0">
      <Card
        :key="activeIndex"
        :front="cards[activeIndex].front"
        :back="cards[activeIndex].back"
      />

      <div class="flex items-center justify-center mt-4 gap-x-5">
        <button 
          @:click="prevCard" 
          :disabled="activeIndex === 0" 
          :class="{ 'text-gray-500 pointer-events-none' : activeIndex === 0 }" 
          aria-label="Previous card" 
          class="text-2xl"
        >
          <ArrowLeftCircleIcon class="w-12 h-12 hover:text-blue-300 transition-colors duration-250"/>
        </button>

        <div class="w-16 text-center">
          <p class="text-lg">
            {{ activeIndex + 1 }} / {{ cards.length }}
          </p>
        </div>

        <button 
          @click="nextCard" 
          :disabled="activeIndex === cards.length - 1" 
          aria-label="Next card" 
          :class="{ 'text-gray-500 pointer-events-none' : activeIndex === cards.length - 1 }" 
          class="text-2xl"
        >
          <ArrowRightCircleIcon class="w-12 h-12 hover:text-blue-300 transition-colors duration-250"/>
        </button>
      </div>
    </div>

  </div>
</template>