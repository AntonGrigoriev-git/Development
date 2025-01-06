<template>
  <div id="app">
    <nav>
      <router-link to="/">Вход</router-link>
      <router-link to="/register">Регистрация</router-link>
    </nav>
    <router-view /> <!-- Здесь будет отображаться текущий компонент маршрута -->
  </div>
</template>

<script>
export default {
  name: 'App', // Имя компонента (опционально)
};
</script>

<style>
  /* Добавить стили */
</style>
