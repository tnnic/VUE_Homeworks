<template>
  <div class="counter">Counter: {{ count }}</div>
  <div class="counter">Double Counter: {{ doubleCount }}</div>
  <button v-on:click="increment" class="button">Increment+</button>
  <button @click="decrement" class="button">Decrement-</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      count: 0,
    };
  },
  emits: ['increment'],
  computed: {
    doubleCount() {
      return this.count * 2;
    },
  },
  methods: {
    increment() {
      this.count++;
      this.$emit('increment', this.count);
    },
    decrement() {
      if (this.count === 0) {
        alert('Достигнут минимум');
        return;
      }
      this.count--;
    },
  },
  watch: {
    count(newValue, oldValue) {
      console.log('new value', newValue);
      console.log('old value', oldValue);
    },
    doubleCount: {
      handler(newValue, oldValue) {
        console.log('new value', newValue);
        console.log('old value', oldValue);
      },
      immediate: true,
    },
  },
});
</script>

<style scoped>
.button {
  background-color: purple;
  color: #fff;
  padding: 10px 20px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  margin: 0 10px;
  cursor: pointer;
  font-size: 16px;
}
</style>
