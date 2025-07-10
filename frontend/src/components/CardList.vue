<script setup lang="ts">
import Card from '../components/Card.vue'

defineProps<{
    cards: {
        front: string;
        back: string;
    }[];
}>();
</script>

<template>
    <div class="flex flex-col justify-center gap-6">
        <Card 
            v-for="(card, index) in cards"
            :key="index"
            :front="card.front"
            :back="card.back"
        />
    </div>
</template>