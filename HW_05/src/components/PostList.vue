<template>
  <div>
    <PostItem v-for="post in visiblePosts" :key="post.id" :post="post" />
    <button @click="toggleShowAll">
      {{ showAll ? 'Показать первые 10' : 'Показать все' }}
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';
import type { IPost } from '@/mocks/types';
import PostItem from './PostItem.vue';

const posts = ref<IPost[]>([]);
const showAll = ref(false);

const visiblePosts = computed(() => (showAll.value ? posts.value : posts.value.slice(0, 10)));

function toggleShowAll() {
  showAll.value = !showAll.value;
}

onMounted(async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  posts.value = await res.json();
});
</script>
