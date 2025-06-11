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
import { defineComponent } from 'vue';
import TheHeader from './components/Header.vue';
import TheSidebar from './components/Sidebar.vue';
import TheMainSection from './components/MainSection.vue';
import TheFooter from './components/Footer.vue';

export default defineComponent({
  name: 'App',
  components: { TheHeader, TheSidebar, TheMainSection, TheFooter },
  data() {
    return {
      isDark: false,
    };
  },
  computed: {
    themeClass() {
      return this.isDark ? 'dark' : 'light';
    },
  },
  methods: {
    toggleTheme() {
      this.isDark = !this.isDark;
    },
  },
});
</script>

<style>
.light { background: #fff; color: #222; min-height: 200px; }
.dark { background: #222; color: #fff; min-height: 200px; }
.layout { display: flex; }
</style>
