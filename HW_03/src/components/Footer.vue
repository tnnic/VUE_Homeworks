<template>
  <footer :class="isDark ? 'dark' : 'light'">
    &copy; 2024 Мой сайт. Все права защищены.
  </footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TheFooter',
  props: {
    isDark: Boolean
  }
})
</script>

<style scoped>
footer { padding: 20px; text-align: center; height: 200px; }
.light { background: #e0e0e0; }
.dark { background: #222; }
</style> 