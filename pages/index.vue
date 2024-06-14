<template>
  <main class="container">
    <h1>Users</h1>
   <section v-for="user of users" :key="user.id" class="users">
    <nuxt-link :to="'/users/' + user.id">{{ user.name }}</nuxt-link>
   </section>
  </main>
</template>

<script setup>
import { useAsyncData } from "nuxt/app";

// const users = ref([]);

const { data } = await useAsyncData("users", () =>
  $fetch("https://jsonplaceholder.typicode.com/users")
);

const users = data.value || [];
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
.users {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #ccc;
  cursor: pointer;
}
</style>
