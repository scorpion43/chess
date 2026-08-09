<template>
  <div class="level-selector">
    <p class="level-selector__elo-title">Choose your elo level:</p>
    <ul class="level-selector__level-list">
      <CGEloItem
        v-for="(elo, index) in levels"
        :elo="elo"
        :chosen="index === choosenEloIndex"
        :key="`level-${index}`"
        @click="chooseElo(index)"
      />
    </ul>
  </div>
</template>
<script setup lang="ts">
import { ref, type Ref } from 'vue'
import CGEloItem from './CGEloItem.vue'

const emit = defineEmits(['chooseLevel'])

const levels: number[] = [1100, 1200, 1300, 1400, 1500, 1600]
const choosenEloIndex: Ref<number> = ref(0)

const chooseElo = (eloIndex: number) => {
  choosenEloIndex.value = eloIndex
  emit('chooseLevel', levels[eloIndex])
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
  &__elo-title {
    text-align: center;
  }
}
</style>
