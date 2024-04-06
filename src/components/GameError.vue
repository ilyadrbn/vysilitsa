<script setup lang="ts">
defineProps<{
  word: string;
  inputLetters: string[];
}>();
</script>
<template>
  <div class="wrong-letters-container">
    <div class="wrong-letters">
      <p>Ошибки</p>
      <span v-for="(letter, index) in inputLetters" :key="index">{{
        word.includes(letter) ? '' : letter
      }}</span>
    </div>
  </div>
</template>
