<template>
  <div class="wrapper">
    <PageHeader :title="text" />
    <section class="main">
      <h2>App</h2>
      <ClickCounter @increment="onIncrement" />
      <div class="user">
        <h2>User</h2>
        <div>Name: {{ user.name }}</div>
        <div>Age: {{ user.age }}</div>
        <button @click="changeName" class="button">Change Name</button>
        <button @click="changeAgeDecrement" class="button">Change Age Decrement</button>
        <button @click="changeAgeIncrement" class="button">Change Age Increment</button>
        <div class="text">Text: {{ text }}</div>
        <div class="textAge" :style="textStyle">Text Age: {{ textAge }}</div>
      </div>
    </section>

    <PageFooter />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import PageHeader from './components/PageHeader.vue';
import PageFooter from './components/PageFooter.vue';
import ClickCounter from './components/ClickCounter.vue';
export default defineComponent({
  components: {
    PageHeader,
    PageFooter,
    ClickCounter,
  },
  data() {
    return {
      user: {
        name: 'John',
        age: 20,
      },
      text: '',
      textAge: '',
    };
  },
  methods: {
    changeName() {
      const names = ['Jane', 'Alice', 'Mary', 'Sarah', 'Emma'];
      this.user.name = names[Math.floor(Math.random() * names.length)];
    },
    changeAge() {
      this.user.age++;
    },
    changeAgeDecrement() {
      this.user.age--;
    },
    changeAgeIncrement() {
      this.user.age++;
    },
    onIncrement(value: number) {
      console.log('increment', value);
    },
  },

  computed: {
    textStyle() {
      return { color: this.user.age <= 18 ? 'red' : 'green' };
    },
  },
  watch: {
    // user: {
    //   handler(newValue, oldValue) {
    //     console.log('new value', newValue);
    //     console.log('old value', oldValue);
    //   },
    //   immediate: true,
    //   deep: true,
    // },
    'user.name': {
      handler(newValue) {
        if (newValue === 'Alice') {
          this.text = 'Alice is a good girl';
        } else {
          this.text = `${newValue} is a bad`;
        }
        // console.log('new name', newValue);
        // console.log('old name', oldValue);
      },
      immediate: true,
    },
    'user.age': {
      handler(newValue) {
        if (newValue > 18) {
          this.textAge = 'Adult';
        } else {
          this.textAge = 'Child';
        }
      },
      immediate: true,
    },
  },
});
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 100vh;
}
.main {
  flex-grow: 1;
  padding: 20px;
  font-size: 20px;
  background-color: #f0f0f0;
  color: #000;
}
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
.textAge {
  color: green;
}
</style>
