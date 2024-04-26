<template>
  <div class="wrong-letters-container" v-if="incorrectLetters.length">
    <div class="wrong-letters">
      <p>Ошибки</p>
      <span> {{ incorrectLetters.join(', ') }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
interface IProps {
  incorrectLetters: string[];
}
defineProps<IProps>();
</script>
