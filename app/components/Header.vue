<template>
  <header class="  w-full text-white flex  justify-around items-center ">
      <div class="  w-[270px] h-[80px] ">
          <img src="/../public/images/logo.png" alt="">
      </div>
      <div class="w-[800px] h-[80px]  flex justify-center items-center gap-5">
          <ul class="flex justify-center items-center gap-10">
            <li class="flex justify-center items-center text-xl text-black font-semibold">
              <NuxtLink 
                to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500">Home</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span>
              </NuxtLink>
            </li>
            <li class="flex justify-center items-center text-xl text-black font-semibold">
              <NuxtLink 
                to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500">Jobs</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span>
              </NuxtLink>

            </li>
            <li class="flex justify-center items-center text-xl text-black font-semibold">
             <NuxtLink 
                to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500">Companies</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span>
              </NuxtLink>
            </li>
            <li class="flex justify-center items-center text-xl text-black font-semibold">
             <NuxtLink 
                to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500">About</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span>
              </NuxtLink>
            </li>
            <li class="flex justify-center items-center text-xl text-black font-semibold">
              <NuxtLink 
                to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500">Contact </span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span>
              </NuxtLink>
            </li>
          </ul>
      </div>
      <div class=" w-[270px] h-[50px] flex justify-center items-center gap-8">
               <i class="fa-solid fa-bars text-3xl text-black"></i>
               <i class="fa-regular fa-circle-user text-3xl text-black"></i>
          </div>
  </header>
</template>

<script setup>
// No JS logic needed yet
</script>
