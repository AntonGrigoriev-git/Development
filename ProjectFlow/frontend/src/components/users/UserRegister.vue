<template>
  <div>
    <h2>Регистрация</h2>
    <form @submit.prevent="register">
      <label for="last_name">Фамилия:</label>
      <input type="text" v-model="lastName" required>

      <label for="first_name">Имя:</label>
      <input type="text" v-model="firstName" required>

      <label for="middle_name">Отчество:</label>
      <input type="text" v-model="middleName" required>

      <label for="email">Email:</label>
      <input type="email" v-model="email" required>

      <label for="password">Пароль:</label>
      <input type="password" v-model="password" required>

      <label for="confirm_password">Подтверждение пароля:</label>
      <input type="password" v-model="confirmPassword" required>

      <button type="submit">Зарегистрироваться</button>
      <p v-if="error" style="color: red;">{{ error }}</p>
      <p v-if="successMessage" style="color: green;">{{ successMessage }}</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      lastName: '',
      firstName: '',
      middleName: '',
      email: '',
      password: '',
      confirmPassword: '',
      error: null,
      successMessage: null,
    };
  },
  methods: {
    async register() {
      // Проверка совпадения паролей
      if (this.password !== this.confirmPassword) {
        this.error = 'Пароли не совпадают.';
        return;
      }
      
      try {
        const response = await fetch('http://localhost:8000/users/api/register/', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            last_name: this.lastName,
            first_name: this.firstName,
            middle_name: this.middleName,
            email: this.email,
            password: this.password,
          }),
        });
        if (!response.ok) {
          const errorData = await response.json(); // Получаем данные об ошибке от сервера
          throw new Error(errorData.error || 'Ошибка регистрации'); // Используем сообщение от сервера
        }
        const data = await response.json(); // Получаем данные об успешной регистрации
        this.successMessage = data.message; // Устанавливаем сообщение об успешной регистрации

        // Задержка перед перенаправлением
        setTimeout(() => {
          this.$router.push('/'); // Перенаправление на страницу входа
        }, 2000);
      } catch (error) {
        this.error = error.message;
      }
    },
  },
};
</script>

<style>

</style>