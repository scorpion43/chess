<template>
  <ul class="chess-navigation">
    <li
      class="chess-navigation__link"
      v-for="link in navLinks"
      :key="link.name"
    >
      <RouterLink :to="{ name: link.name }">
        {{ link.title }}
      </RouterLink>
    </li>
  </ul>
</template>
<script setup lang="ts">
import type { NavLink } from '@/types/navigation'

const navLinks: NavLink[] = [
  {
    title: 'New Game',
    name: 'game',
  },
]
</script>
