<template>
  <div class="wrappen">
    <PageHeader />
    <section class="main-section"><HomeView /></section>

    <Footer />
  </div>
</template>

<script setup lang="ts">
import PageHeader from './components/PageHeader.vue';
import Footer from './components/PageFooter.vue';
import HomeView from './views/HomeView.vue';
</script>

<style scoped>
.wrappen {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.main-section {
  flex: 1;
  padding: 20px;
  background-color: wheat;
  font-size: 14px;
  color: black;
}
</style>
