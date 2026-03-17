<template>
  <div class="level-selector">
    <ul class="level-selector__level-list">
      <li
        class="level-selector__level-item"
        v-for="(item, index) in levels"
        :key="`level-${index}`"
        @click="chooseLevel(index)"
      >
        <p class="level-selector__label">{{ index + 1 }}</p>
        <p class="level-selector__elo">elo: {{ item }}</p>
      </li>
    </ul>
  </div>
</template>
<script setup lang="ts">
import { ref, type Ref } from 'vue'

const emit = defineEmits(['chooseLevel'])

const levels: number[] = [1100, 1200, 1300, 1400, 1500, 1600]
const choosenLevelIndex: Ref<number> = ref(0)

const chooseLevel = (levelIndex: number) => {
  choosenLevelIndex.value = levelIndex
  emit('chooseLevel', levels[choosenLevelIndex.value])
}
</script>
<style lang="scss">
.level-selector {
  &__level-list {
    display: flex;
    list-style-type: none;
    gap: 4px;
  }
  &__level-item {
    border: 1px solid black;
    border-radius: 50%;
    padding: 20px 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
