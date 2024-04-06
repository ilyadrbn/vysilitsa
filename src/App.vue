<script setup lang="ts">
import GameHeader from './components/GameHeader.vue';
import GameFigure from './components/GameFigure.vue';
import GameError from './components/GameError.vue';
import GameWord from './components/GameWord.vue';
import GamePopup from './components/GamePopup.vue';
import GameNotification from './components/GameNotification.vue';
import { ref } from 'vue';

const word = ref('илья');
const inputLetters = ref<string[]>([]);
const isRepeatLetter = ref(false);
interface Game {
  word: string;
  inputLetters: string[];
}

window.addEventListener('keydown', ({ key }) => {
  if (/[\u0400-\u04FF]/.test(key)) {
    isRepeatLetter.value = inputLetters.value.includes(key.toLowerCase());
    inputLetters.value.push(key.toLowerCase());
  }
});
</script>

<template>
  <p>{{ word }}</p>
  <div class="game-container">
    <GameHeader />
    <GameFigure />
    <GameError :word="word" :inputLetters="inputLetters" />
    <GameWord :word="word" :inputLetters="inputLetters" />
  </div>
  <GamePopup v-if="false" />
  <GameNotification v-if="isRepeatLetter" />
</template>
