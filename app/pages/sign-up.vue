<script setup>
import { ref } from "vue"


const email = ref("chorkbora4@gmail.com")
const password = ref("bora1234")

const handleLogin = () => {
  console.log("Logged In:", email.value)
}

</script>

<template>
  <div class="flex items-top justify-center pt-20 pb-20 mb-20">
    <div class="bg-white p-8 rounded-2xl shadow-md w-96">
      <h3 class="text-2xl font-bold mb-6 text-center">Create Account</h3>

      <form @submit.prevent="handleSignup" class="space-y-4">
        <input class="w-full p-3 border rounded-lg"
          v-model="name"
          type="text"
          placeholder="Full Name"
          required
        />

        <input class="w-full p-3 border rounded-lg"
          v-model="email"
          type="email"
          placeholder="Email"
          required
        />

        <input class="w-full p-3 border rounded-lg"
          v-model="password"
          type="password"
          placeholder="Password"
          required
        />

        
        <button class="w-full bg-blue-600 text-white p-3 rounded-lg" type="submit">
            Sign Up
        </button> 
    </form>


      <p class="text-sm text-center mt-4">
        Already have an account?
        <NuxtLink to="/login" class="text-blue-600">Login</NuxtLink>
      </p>
    </div>
  </div>
</template>


