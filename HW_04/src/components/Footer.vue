<template>
  <footer :class="props.isDark ? 'dark' : 'light'">
    &copy; 2024 Мой сайт. Все права защищены.
  </footer>
</template>

<script setup lang="ts">
interface Props {
  isDark: boolean;
}
const props = defineProps<Props>();
defineOptions({ name: 'TheFooter' });
</script>

<style scoped>
footer { padding: 20px; text-align: center; height: 200px; }
.light { background: #e0e0e0; }
.dark { background: #222; }
</style> 