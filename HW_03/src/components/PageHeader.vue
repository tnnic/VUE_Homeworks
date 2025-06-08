<template>
  <header class="header">{{ title }}</header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    title: {
      type: String,
      required: false,
      default: 'Header',
    },
  },
});
</script>

<style scoped>
.header {
  height: 150px;
  background-color: green;
  font-size: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
