<template>
  <li
    class="level-item"
    :class="{ chosen: chosen }"
  >
    <p class="level-item__elo">{{ elo }}</p>
  </li>
</template>
<script setup lang="ts">
defineProps({
  elo: {
    type: Number,
    reuqired: true,
  },
  chosen: {
    type: Boolean,
    default: false,
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
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
  border: none;
  position: relative;
  &::after {
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    border-radius: 50%;
    opacity: 0;
    transition: opacity 0.3s ease-out;
    box-shadow:
      rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset,
      rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
  }
  &:hover {
    &::after {
      opacity: 1;
    }
  }
  &.chosen {
    &:after {
      opacity: 1;
      box-shadow:
        rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset,
        rgba(242, 32, 32, 0.3) 0px 50px 100px -18px inset;
    }
  }
  &__elo {
    z-index: 999;
  }
}
</style>
