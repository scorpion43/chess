<template>
  <div class="level-selector">
    <ul class="level-selector__level-list">
      <CGEloItem
        v-for="(elo, index) in levels"
        :elo="elo"
        :key="`level-${index}`"
        @click="chooseLevel(elo)"
      />
    </ul>
  </div>
</template>
<script setup lang="ts">
import { ref, type Ref } from 'vue'
import CGEloItem from './CGEloItem.vue'

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
    padding: 0;
    width: fit-content;
    margin: 0 auto;
    list-style-type: none;
    gap: 5px;
    display: grid;
    grid-template-columns: 130px 130px 130px;
    grid-template-rows: 130px 130px 130px;
    place-items: center;
  }
}
</style>
