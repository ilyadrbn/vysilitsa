<template>
  <div v-if="isVisible" class="popup-container">
    <div class="popup">
      <h2 v-if="gameStatus === 'win'">Поздравляю, вы победили! 😃</h2>
      <h2 v-else>Вы проиграли. 😕</h2>
      <h3>Имя:</h3>
      <button @click="$emit('play-again')">Сыграть еще раз</button>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';
const isVisible = ref<boolean>(false);

type Status = 'win' | 'lose';

const gameStatus = ref<Status | null>(null);

const showPopup = (status: Status) => {
  gameStatus.value = status;
  isVisible.value = true;
};

defineExpose({ showPopup });

defineEmits({
  'play-again': () => true
});
</script>
