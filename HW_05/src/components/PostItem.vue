<template>
  <div class="post-item">
    <strong>{{ post.title }}</strong>
    <p>{{ post.body }}</p>
  </div>
</template>

<script setup lang="ts">
import type { IPost } from '../mocks/types';

defineProps<{ post: IPost }>();
</script>

<style scoped>
.post-item {
  margin-bottom: 16px;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
}
</style>
