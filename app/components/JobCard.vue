<template>
  <div 
    :class="['p-5 rounded-[32px] flex flex-col justify-between h-full transition-transform hover:scale-[1.02]', bgColor]"
  >
    <div class="flex justify-between items-start">
      <span class="bg-white px-4 py-2 rounded-full text-[12px] font-medium text-gray-800">
        {{ date }}
      </span>
      <button class="bg-white w-9 h-9 rounded-full flex items-center justify-center hover:bg-gray-100 transition-colors">
        <i class="fa-regular fa-bookmark text-sm"></i>
      </button>
    </div>

    <div class="mt-4">
      <div class="flex justify-between items-center">
        <span class="text-sm font-semibold text-gray-900">{{ company }}</span>
        <div class="w-8 h-8 rounded-full bg-white flex items-center justify-center shadow-sm">
           <i :class="[companyIcon, 'text-lg']"></i>
        </div>
      </div>
      <h3 class="text-xl font-bold text-gray-900 leading-tight mt-1 max-w-[150px]">
        {{ title }}
      </h3>
    </div>

    <div class="flex flex-wrap gap-2 mt-4">
      <span 
        v-for="tag in tags" :key="tag" 
        class="border border-gray-400/30 px-3 py-1 rounded-full text-[11px] font-medium text-gray-700"
      >
        {{ tag }}
      </span>
    </div>

    <div class="flex justify-between items-center mt-6">
      <div class="flex flex-col">
        <span class="text-lg font-bold text-gray-900">${{ price }}/hr</span>
        <span class="text-[11px] text-gray-500 font-medium">{{ location }}</span>
      </div>
      <button class="bg-black text-white px-6 py-3 rounded-2xl text-xs font-bold hover:bg-gray-800 transition-colors">
        Details
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  date: String,
  company: String,
  companyIcon: String, // Font Awesome class like 'fa-brands fa-amazon'
  title: String,
  tags: Array,
  price: [Number, String],
  location: String,
  bgColor: String // Tailwind class like 'bg-[#FFE2C5]'
})
</script>