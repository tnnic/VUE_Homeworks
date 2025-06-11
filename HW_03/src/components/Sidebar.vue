<template>
  <aside :class="isDark ? 'dark' : 'light'">
    <h3>Навигация</h3>
    <ul>
      <li>Главная</li>
      <li>Профиль</li>
      <li>Сообщения</li>
      <li>Настройки</li>
    </ul>
  </aside>
</template>

<script lang="ts">
export default {
  name: 'TheSidebar',
  props: ['isDark']
}
</script>

<style scoped>
aside { width: 200px; padding: 20px; height: 600px;}
.light { background: #f0f0f0; }
.dark { background: #333; }
ul { list-style: none; padding: 0; }
li { margin-bottom: 10px; }
</style> 