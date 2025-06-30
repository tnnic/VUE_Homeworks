<template>
  <div class="wrapper">
    <PageHeader />
    <section class="section-main">
      <UserForm />
    </section>
    <PageFooter />
  </div>
</template>

<script setup lang="ts">
import PageHeader from './components/PageHeader.vue';
import PageFooter from './components/PageFooter.vue';
import UserForm from './components/UserForm.vue';
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.section-main {
  flex: 1;
  background-color: wheat;
}
</style>
