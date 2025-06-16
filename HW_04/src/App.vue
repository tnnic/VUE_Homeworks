<template>
  <div :class="themeClass">
    <TheHeader :isDark="isDark" @toggle-theme="toggleTheme" />
    <div class="layout">
      <TheSidebar :isDark="isDark" />
      <TheMainSection :isDark="isDark" />
    </div>
    <TheFooter :isDark="isDark" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';
import TheHeader from './components/Header.vue';
import TheSidebar from './components/Sidebar.vue';
import TheMainSection from './components/MainSection.vue';
import TheFooter from './components/Footer.vue';

export default defineComponent({
  name: 'App',
  components: { TheHeader, TheSidebar, TheMainSection, TheFooter },
  setup() {
    const isDark = ref(false);
    const themeClass = computed(() => (isDark.value ? 'dark' : 'light'));
    function toggleTheme() {
      isDark.value = !isDark.value;
    }
    return {
      isDark,
      themeClass,
      toggleTheme,
    };
  },
});
</script>

<style>
.light { background: #fff; color: #222; min-height: 200px; }
.dark { background: #222; color: #fff; min-height: 200px; }
.layout { display: flex; }
</style>
