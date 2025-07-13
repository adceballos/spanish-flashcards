<script setup lang="ts">
import { ref } from 'vue';
// TODO(maybe): auto flip component every few seconds rather than on hover
const titlesInOtherLanguages = [
  { text: "Giro Fluido", language: "Spanish" },
  { text: "Retournement Fluide", language: "French" },
  { text: "Capovolgimento Fluido", language: "Italian" },
  { text: "流暢な反転", language: "Japanese" },
  { text: "유창한 뒤집기", language: "Korean" },
  { text: "Flüssige Wendung", language: "German" },
  { text: "流畅翻转", language: "Mandarin Chinese" },
  { text: "Virada Fluente", language: "Portuguese" },
  { text: "Плавный переворот", language: "Russian" },
];

// currentWord will store the randomly chosen word object
const currentTitleInOtherLanguage = ref(titlesInOtherLanguages[0]);

const getRandomWord = () => {
  let newTitleInOtherLanguage;
  do {
    newTitleInOtherLanguage = titlesInOtherLanguages[Math.floor(Math.random() * titlesInOtherLanguages.length)];
  } while (newTitleInOtherLanguage.text === currentTitleInOtherLanguage.value.text); // avoid immediate repeat
  
  currentTitleInOtherLanguage.value = newTitleInOtherLanguage;
};


</script>

<template>
    <div class="flex justify-center">
        <div class="relative w-100 h-76 -rotate-30">
            <div class="w-full h-full bg-gray-500 rounded-2xl shadow-2xl">
            </div>
        </div>
    </div>

    <div class="flex justify-center -mt-80">
        <div class="relative w-100 h-76 -rotate-15">
            <div class="w-full h-full bg-gray-500 rounded-2xl shadow-2xl">
            </div>
        </div>
    </div>

    <div class="perspective-midrange flex justify-center -mt-80">
        <div @mouseenter="getRandomWord" class="relative w-100 h-76 duration-500 transform-3d transition-transform hover:rotate-x-180">
            <div class="cinzel tracking-wider absolute w-full h-full backface-hidden bg-gray-500 text-white rounded-2xl flex items-center justify-center shadow-2xl text-4xl">
                Fluent Flip
            </div>

            <div class="absolute w-full h-full backface-hidden bg-slate-700 text-white rounded-2xl justify-center shadow-2xl transform rotate-x-180 flex flex-col items-center">
                <h1 class="cinzel text-4xl text-center">{{ currentTitleInOtherLanguage.text }}</h1>
                <h1 class="text-lg text-center text-gray-300 font-light italic">Translation of "Fluent Flip" in {{ currentTitleInOtherLanguage.language }}</h1>
                <p class="cinzel text-2xl mt-4">Developed by <a href="https://adrianceballos.com" target="_blank" rel="noopener" class="text-blue-300">Adrian</a></p>
            </div>
        </div>
    </div>
</template>