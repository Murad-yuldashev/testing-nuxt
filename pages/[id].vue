<template>
  <main class="container">
    <h1>User Details</h1>
    <div v-if="user">
      <h2>{{ user.name }}</h2>
      <p><strong>Email:</strong> {{ user.email }}</p>
      <p><strong>Phone:</strong> {{ user.phone }}</p>
      <p><strong>Website:</strong> {{ user.website }}</p>
    </div>
    <nuxt-link to="/users">Back to Users</nuxt-link>
  </main>
</template>

<script setup>
import { useAsyncData } from "nuxt/app";

const userId = $route.params.id;
const user = ref(null);

// Fetch user data on component mount
onMounted(async () => {
  const { data } = await useAsyncData(`user-${userId}`, () =>
    $fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
  );
  user.value = data;
});
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
</style>
