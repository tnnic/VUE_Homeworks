<template>
  <form :class="$style.form" @submit.prevent="onSubmit">
    <label :class="$style.label">
      Фамилия
      <input type="text" name="lastName" :class="$style.input" v-model="lastName" />
    </label>
    <label :class="$style.label">
      Имя
      <input type="text" name="firstName" :class="$style.input" v-model="firstName" />
    </label>
    <label :class="$style.label">
      Телефон
      <input
        type="tel"
        name="phone"
        :class="[$style.input, phoneError ? $style.error : '']"
        v-model="phone"
      />
      <div v-if="phoneError" :class="$style.errorText">{{ phoneError }}</div>
    </label>
    <label :class="$style.label">
      Email
      <input
        type="email"
        name="email"
        :class="[$style.input, emailError ? $style.error : '']"
        v-model="email"
      />
      <div v-if="emailError" :class="$style.errorText">{{ emailError }}</div>
    </label>
    <div :class="[$style['checkbox-row']]">
      <input type="checkbox" name="consent" v-model="consent" />
      <span>Согласие на обработку персональных данных</span>
    </div>
    <div v-if="consentError" :class="$style.errorText">{{ consentError }}</div>
    <button type="submit" :class="$style.button">Отправить</button>
  </form>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const lastName = ref('');
const firstName = ref('');
const phone = ref('');
const email = ref('');
const consent = ref(false);

const phoneError = ref('');
const emailError = ref('');
const consentError = ref('');

async function onSubmit() {
  // Сброс ошибок
  consentError.value = '';
  phoneError.value = '';
  emailError.value = '';

  // Валидация согласия
  if (!consent.value) {
    consentError.value = 'Необходимо согласие на обработку данных';
  }

  // Валидация телефона
  if (!phone.value) {
    phoneError.value = 'Необходимо ввести телефон';
  } else if (!/^\+?\d{10,15}$/.test(phone.value)) {
    phoneError.value = 'Некорректный формат телефона';
  }

  // Валидация email
  if (!email.value) {
    emailError.value = 'Необходимо ввести email';
  } else if (!/^[\w-.]+@[\w-]+\.[a-z]{2,}$/i.test(email.value)) {
    emailError.value = 'Некорректный формат email';
  }

  // Если есть ошибки — не отправлять
  if (phoneError.value || emailError.value || consentError.value) {
    return;
  }

  // Отправка данных через fetch
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        lastName: lastName.value,
        firstName: firstName.value,
        phone: phone.value,
        email: email.value,
        consent: consent.value,
      }),
    });

    if (response.ok) {
      alert('Данные успешно отправлены!');
      // Можно сбросить форму, если нужно:
      lastName.value = '';
      firstName.value = '';
      phone.value = '';
      email.value = '';
      consent.value = false;
    } else {
      alert('Ошибка отправки данных!');
    }
  } catch {
    alert('Ошибка сети!');
  }
}
</script>

<style module lang="scss">
.form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: 40px auto;
  padding: 24px;
  background: #fffbe6;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.07);
  gap: 16px;
}
.label {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.input {
  width: 100%;
  padding: 8px 12px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
.checkbox-row {
  display: flex;
  align-items: center;
  gap: 8px;
}
.button {
  width: 100%;
  padding: 10px 0;
  font-size: 1rem;
  background: #ffd600;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 8px;
  transition: background 0.2s;
}
.button:hover {
  background: #ffb300;
}
.error {
  border-color: #e53935;
}
.errorText {
  color: #e53935;
  font-size: 0.9em;
  margin-top: 2px;
}
</style>
