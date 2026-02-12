<template>
  <header class="bg-blue-500 text-white p-4">
    <nav class="container mx-auto flex justify-between items-center">
      <h1 class="text-xl font-bold">My Nuxt App</h1>
      <ul class="flex gap-4">
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink to="/about">About</NuxtLink></li>
        <li><NuxtLink to="/contact">Contact</NuxtLink></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
// No JS logic needed yet
</script>
