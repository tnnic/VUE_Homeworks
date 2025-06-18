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

<script setup lang="ts">
import TheHeader from './components/Header.vue';
import TheSidebar from './components/Sidebar.vue';
import TheMainSection from './components/MainSection.vue';
import TheFooter from './components/Footer.vue';
import { ref, computed } from 'vue';

defineOptions({ name: 'App' });

const isDark = ref(false);
const themeClass = computed(() => (isDark.value ? 'dark' : 'light'));
function toggleTheme() {
  isDark.value = !isDark.value;
}
</script>

<style>
.light { background: #fff; color: #222; min-height: 200px; }
.dark { background: #222; color: #fff; min-height: 200px; }
.layout { display: flex; }
</style>
