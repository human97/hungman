<script setup lang="ts">
import { ref } from 'vue'
import type { GameStatus } from '@/types/GameStatus'

interface Props {
  word: string | 0
}

defineProps<Props>()

const gameStatus = ref<GameStatus | null>(null)
const isVisible = ref<boolean>(false)

const open = (status: GameStatus) => {
  gameStatus.value = status
  isVisible.value = true
}
const close = () => {
    isVisible.value = false
}

defineExpose({ 
    open, 
    close 
})

const emit = defineEmits<{
    (e: 'restart'): void
  }>()
</script>

<template>
    <div 
      class="popup-container" 
      v-show="isVisible"
    >
      <div class="popup">
        <h2 v-if="gameStatus === 'win'">Поздравляю, вы победили! 😃</h2>
        <template v-else>
          <h2>Вы проиграли. 😕</h2>
          <h3>...имя: {{ word }}</h3>
        </template>
        <button @click="emit('restart')">Сыграть еще раз</button>
      </div>
    </div>  
</template>