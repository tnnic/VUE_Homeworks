<template>
  <footer :class="isDark ? 'dark' : 'light'">
    &copy; 2024 Мой сайт. Все права защищены.
  </footer>
</template>

<script lang="ts">
export default {
  name: 'TheFooter',
  props: ['isDark']
}
</script>

<style scoped>
footer { padding: 20px; text-align: center; height: 200px; }
.light { background: #e0e0e0; }
.dark { background: #222; }
</style> 