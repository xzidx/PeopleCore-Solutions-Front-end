<script setup>
import { ref } from "vue"


const email = ref("")
const password = ref("")

const handleLogin = () => {
  console.log("Logged In:", email.value)
}

</script>

<template>
    <div class="flex justify-center items-center w-[100%] h-screen">
    <div class="bg-white w-110 p-8 shadow-md border rounded-lg w-[700px]">
      <h3 class="text-2xl font-bold mb-6 text-center">Login</h3>

      <form @submit.prevent="handleLogin" class="space-y-4">

        <div class="flex justify-center items-center gap-4">
          <input class="w-full p-3 border rounded-lg"
            v-model="name"
            type="text"
            placeholder="Last Name"
            required
          />
          <input class="w-full p-3 border rounded-lg"
            v-model="firstName"
            type="text"
            placeholder="First Name"
            required
          />

        </div>

        <input class="w-full p-3 border rounded-lg"
          v-model="email"
          type="email"
          placeholder="Your Email or number phone"
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
        <NuxtLink to="/sign-up" class="text-blue-600">Make Account</NuxtLink>
      </p>
    </div>
  </div>
</template>


