<template>
  <main :class="props.isDark ? 'dark' : 'light'">
    <h1>Добро пожаловать!</h1>
    <p>Это главная секция вашего сайта. Здесь может быть любой контент: новости, статьи, описание сервиса и т.д.</p>
  </main>
</template>

<script setup lang="ts">
interface Props {
  isDark: boolean;
}
const props = defineProps<Props>();
</script>

<style scoped>
main { flex: 1; padding: 20px; }
.light { background: #fafafa; }
.dark { background: #444; }
</style> 