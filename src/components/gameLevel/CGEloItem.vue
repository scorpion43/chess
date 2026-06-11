<template>
  <li class="level-item">
    <p class="level-item__elo">{{ elo }}</p>
  </li>
</template>
<script setup lang="ts">
defineProps({
  elo: {
    type: Number,
    reuqired: true,
  },
})
</script>
<style lang="scss">
.level-item {
  border: 1px solid black;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-width: 100px;
  min-height: 100px;
  max-width: 120px;
  min-width: 120px;
  aspect-ratio: 1/1;
}
</style>
