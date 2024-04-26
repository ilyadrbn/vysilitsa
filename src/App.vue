<template>
  <div class="game-container">
    <GameHeader />
    <GameFigure :incorrect-letters-length="incorrectLetters.length" />
    <GameErrorList :incorrect-letters="incorrectLetters" />
    <GameWord :word="word" :correct-letters="correctLetters" />
  </div>
  <GamePopup v-if="false" />
  <GameNotification v-if="showNotification" />
</template>

<script setup lang="ts">
import GameHeader from './components/GameHeader.vue';
import GameFigure from './components/GameFigure.vue';
import GameErrorList from './components/GameErrorList.vue';
import GameWord from './components/GameWord.vue';
import GamePopup from './components/GamePopup.vue';
import GameNotification from './components/GameNotification.vue';

import { computed, ref } from 'vue';

const word = ref('василий');
const letters = ref<string[]>([]);

const correctLetters = computed(() =>
  letters.value.filter((letter) => word.value.includes(letter))
);
const incorrectLetters = computed(() =>
  letters.value.filter((letter) => !word.value.includes(letter))
);

const showNotification = ref<boolean>(false);

window.addEventListener('keydown', ({ key }) => {
  if (/[а-яА-ЯёЁ]$/.test(key)) {
    if (letters.value.includes(key.toLowerCase())) {
      showNotification.value = true;
      return;
    }
    showNotification.value = false;
    letters.value.push(key.toLowerCase());
  }
});
</script>
