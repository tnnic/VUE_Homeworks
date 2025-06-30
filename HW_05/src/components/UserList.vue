<template>
  <div class="user-div">
    <UserItem v-for="user in visibleUsers" :key="user.id" :user="user" />
    <button @click="toggle">
      {{ showAll ? 'Показать первые 10' : 'Показать всех' }}
    </button>
  </div>
</template>

<script setup lang="ts">
import { usersList } from '@/mocks/usersList';
import { ref, computed } from 'vue';
import UserItem from './UserItem.vue';

const showAll = ref(false);
const visibleUsers = computed(() => (showAll.value ? usersList : usersList.slice(0, 10)));
const toggle = () => {
  showAll.value = !showAll.value;
};
</script>

<style scoped>
/* .user-div {
  flex: 1;
  padding: 20px;
  background-color: wheat;
  font-size: 32px;
  color: black;
} */
</style>
