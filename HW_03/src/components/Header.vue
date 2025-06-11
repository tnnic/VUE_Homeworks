<template>
  <header>
    <span class="site-title">Мой сайт</span>
    <button @click="$emit('toggle-theme')">
      Переключить тему
    </button>
  </header>
</template>

<script lang="ts">
export default {
  name: 'TheHeader',
  props: ['isDark']
}
</script>

<style scoped>
header {
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.site-title {
  font-size: 1.5rem;
  font-weight: bold;
}
button { padding: 10px 20px; }
</style> 