<template>
  <div class="user-item">
    <strong>{{ user.name }}</strong> — {{ user.email }}
  </div>
</template>

<script setup lang="ts">
import type { IUser } from '@/mocks/types';

defineProps<{ user: IUser }>();
</script>

<style scoped>
.user-item {
  padding: 8px 0;
  border-bottom: 1px solid #eee;
}
</style>
