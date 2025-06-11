<template>
  <main :class="isDark ? 'dark' : 'light'">
    <h1>Добро пожаловать!</h1>
    <p>Это главная секция вашего сайта. Здесь может быть любой контент: новости, статьи, описание сервиса и т.д.</p>
  </main>
</template>

<script lang="ts">
export default {
  name: 'TheMainSection',
  props: ['isDark']
}
</script>

<style scoped>
main { flex: 1; padding: 20px; }
.light { background: #fafafa; }
.dark { background: #444; }
</style> 