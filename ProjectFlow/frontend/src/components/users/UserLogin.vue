<template>
  <div>
    <h2>Вход</h2>
    <form @submit.prevent="login">
      <label for="email">Email:</label>
      <input type="email" v-model="email" required>
      <label for="password">Пароль:</label>
      <input type="password" v-model="password" required>
      <button type="submit">Войти</button>
      <p v-if="error" style="color: red;">{{ error }}</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      error: null,
    };
  },
  methods: {
    async login() {
      try {
        const response = await fetch('http://localhost:8000/users/api/login/', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            email: this.email,
            password: this.password,
          }),
        });
        if (!response.ok) {
          const errorData = await response.json(); // Получаем данные об ошибке от сервера
          throw new Error(errorData.error || 'Ошибка входа'); // Используем сообщение от сервера
        }
        this.$router.push('/home');
      } catch (error) {
        this.error = error.message;
      }
    },
  },
};
</script>

<style>

</style>