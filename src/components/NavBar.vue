<template>
  <nav class="bg-white dark:bg-gray-800 shadow">
    <div class="space-x-4">
      <router-link to="/" class="hover:underline">Home</router-link>
      <router-link to="/cart" class="hover:underline">Cart</router-link>
    </div>
    <div class="container mx-auto px-4 py-3 flex justify-between items-center">
      <h1 class="text-lg font-bold">
        <router-link to="/">My E-Commerce</router-link>
      </h1>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar'
};
</script>
