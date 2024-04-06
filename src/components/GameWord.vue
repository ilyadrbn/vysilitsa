<script setup lang="ts">
defineProps<{
  word: string;
  inputLetters: string[];
}>();
</script>

<template>
  <div class="word">
    <span v-for="(letter, index) in word" :key="index" class="letter">{{
      inputLetters.includes(letter) ? letter : ''
    }}</span>
  </div>
</template>
