<template>
  <div class="w-full max-w-base h-[500px] bg-white rounded-[2rem] shadow-sm border border-gray-400 p-8 font-sans flex-row items-center justify-center ">
    
    <div class="flex justify-between items-start mb-6">
      <div class="w-14 h-14 rounded-full border border-gray-500 flex items-center justify-center p-2">
        <img :src="logoUrl" class="w-8">
      </div>
      <button class="px-4 py-2 border border-gray-500 rounded-xl text-sm font-medium text-gray-500">Save</button>
    </div>

    <div class="mb-6">
      <div class="flex items-center gap-2 mb-1">
        <h2 class="text-lg font-bold text-black">{{ company }}</h2>
        <span class="text-gray-400 text-sm">{{ postedAt }}</span>
      </div>
      <h1 class="text-2xl font-bold text-gray-900 leading-tight underline">{{ jobTitle }}</h1>
    </div>

    <div class="flex gap-2 mb-10">
      <span v-for="tag in tags" :key="tag" class="px-4 py-2 bg-gray-100 rounded-xl text-sm font-semibold">
        {{ tag }}
      </span>
    </div>
    <div class="mb-6">
        <p class="text-gray-600 text-lg leading-relaxed">
          {{ info }}
        </p>
      </div>
    <div class="border-t border-gray-100 pt-8 flex items-center justify-between">
      <div>
        <p class="text-xl font-bold text-black">${{ salary }}/hr</p>
        <p class="text-gray-400 text-sm">{{ location }}</p>
      </div>
      <button class="bg-blue-500 text-white px-8 py-4 rounded-2xl font-bold">Apply now</button>
    </div>
  </div>
</template>

<script setup>
// This defines the "slots" you can fill in index.vue
defineProps({
  company: String,
  logoUrl: String,
  postedAt: String,
  jobTitle: String,
  info: String, 
  tags: Array,
  salary: String,
  location: String
})
</script>