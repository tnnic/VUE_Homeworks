<template>
  <header>
    <span class="site-title">Мой сайт</span>
    <button @click="$emit('toggle-theme')">
      Переключить тему
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TheHeader',
  props: {
    isDark: Boolean
  },
  setup(props, { emit }) {
    function toggleTheme() {
      emit('toggle-theme');
    }
    return {
      toggleTheme,
    };
  },
});
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