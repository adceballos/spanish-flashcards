<script setup lang="ts">
import { type Ref, ref, onMounted, onUnmounted } from 'vue';

defineProps<{ 
  front: string;
  back: string;
}>();

// explicitly typed for practice, can be written as 'const flipped = ref(false)' for implicit
const isFlipped: Ref<Boolean> = ref(false);

const handleKey = (e: KeyboardEvent) => {
  if (e.key === "ArrowUp") {
    isFlipped.value = !isFlipped.value
  } else if (e.key === "ArrowDown") {
    isFlipped.value = !isFlipped.value
  }
};

onMounted(() => {
  window.addEventListener("keydown", handleKey)
});

onUnmounted(() => {
  window.removeEventListener("keydown", handleKey)
});
</script>

<template>
  <div class="flex flex-col justify-center gap-8">
    <div
      class="w-120 h-84 perspective-distant"
    >
      <div @click="isFlipped = !isFlipped" :class="{ 'rotate-x-180': isFlipped }" class="relative w-full h-full transition-transform duration-300 transform-3d">
        
        <div class="absolute w-full h-full backface-hidden bg-gray-500 text-white rounded-2xl shadow-xl flex items-center justify-center flex-col">
          <h1 class="text-5xl">{{ front }}</h1>
        </div>

        <div class="absolute w-full h-full backface-hidden rotate-x-180 bg-slate-700 text-white rounded-2xl shadow-xl flex items-center justify-center flex-col">
          <h1 class="text-5xl">{{ back }}</h1>
        </div>

      </div>
    </div>
  </div>
</template>