<template>
  <div>
    <h2>Добро пожаловать</h2>
    <p>Вы успешно вошли в систему!</p>
    <button @click="logout">Выйти</button>
  </div>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$router.push('/');
    },
  },
};
</script>

<style>

</style>