<template>
  <div class="min-h-screen bg-[#F8F9FB] p-6 md:p-12 font-sans flex justify-center items-center mt-[50px]">
    <div class="w-[90%] h-auto mx-auto">
      
      <header class="mb-12 flex flex-col md:flex-row justify-between items-center gap-6">
        <div class="space-y-2">
          <h1 class="text-4xl font-black text-slate-900 tracking-tight">Browse Companies</h1>
        </div>
        
        <div class="w-full md:w-96 relative">
          <input 
            v-model="searchQuery"
            type="text" 
            placeholder="Search by company name..." 
            class="w-full pl-12 pr-4 py-3 bg-white border border-slate-200 rounded-2xl focus:ring-2 focus:ring-blue-500 outline-none transition-all shadow-sm"
          />
          <span class="absolute left-4 top-1/2 -translate-y-1/2 text-slate-400">
            <i class="fa-solid fa-magnifying-glass"></i>
          </span>
        </div>
      </header>

      <!-- Loading state -->
      <div v-if="loading" class="text-center py-20">
        <div class="inline-block animate-spin rounded-full h-8 w-8 border-4 border-blue-500 border-t-transparent"></div>
        <p class="mt-4 text-slate-600">Loading companies...</p>
      </div>

      <!-- Error state -->
      <div v-else-if="error" class="text-center py-20">
        <p class="text-red-500">{{ error }}</p>
        <button 
          @click="fetchCompanies" 
          class="mt-4 px-6 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600"
        >
          Try Again
        </button>
      </div>

      <!-- Companies grid -->
      <div v-else-if="paginatedCompanies.length > 0" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
        <div 
          v-for="company in paginatedCompanies" 
          :key="company.documentId"
          @click="goToDetail(company)"
          class="group bg-white rounded-[2.5rem] p-8 border border-slate-100 shadow-sm hover:shadow-xl hover:shadow-indigo-900/5 hover:-translate-y-1 transition-all duration-300 cursor-pointer"
        >
          <div class="flex justify-between items-start mb-6">
            <div class="w-16 h-16 bg-slate-50 rounded-2xl flex items-center justify-center p-3 border border-slate-100 group-hover:border-indigo-100 transition-colors">
              <img :src="company.logo" :alt="company.name" class="w-full h-auto object-contain" />
            </div>
            <span class="bg-blue-500 text-white text-[10px] font-black uppercase px-2 py-1 rounded-md">
              {{ company.jobsCount || '0' }} Jobs
            </span>
          </div>
          <div class="space-y-1">
            <h2 class="text-xl font-bold text-slate-800 group-hover:text-blue-500 transition-colors">
              {{ company.name }}
            </h2>
            <p class="text-sm text-slate-400 flex items-center gap-1">
              📍 {{ company.location || 'Remote' }}
            </p>
          </div>
          <p class="mt-4 text-sm text-slate-500 line-clamp-2 leading-relaxed">
            {{ company.description || 'No description available' }}
          </p>
          <div v-if="company.tags && company.tags.length" class="flex flex-wrap gap-2 mt-6">
            <span 
              v-for="tag in company.tags" 
              :key="tag" 
              class="px-3 py-1 bg-slate-100 text-slate-500 text-[10px] font-bold rounded-lg"
            >
              {{ tag }}
            </span>
          </div>
        </div>
      </div>

      <!-- No results -->
      <div v-else class="text-center py-20">
        <p class="text-slate-500">No companies found matching your search.</p>
      </div>

      <!-- Pagination -->
      <div v-if="totalPages > 0 && !loading" class="mt-16 flex flex-wrap items-center justify-center gap-6 bg-white p-4 rounded-2xl shadow-sm border border-slate-100">
        <div class="flex items-center gap-4">
          <button 
            @click="currentPage > 1 ? currentPage-- : null" 
            :disabled="currentPage === 1" 
            class="text-sm font-medium text-slate-400 hover:text-slate-900 disabled:opacity-30 disabled:cursor-not-allowed transition-colors"
          >
            Previous
          </button>
          
          <div class="flex items-center gap-1">
            <button 
              v-for="page in visiblePages" 
              :key="page" 
              @click="typeof page === 'number' ? currentPage = page : null" 
              :class="[
                currentPage === page ? 'border-blue-500 text-blue-600 ring-1 ring-blue-500' : 'border-transparent text-slate-600 hover:bg-slate-50',
                page === '...' ? 'cursor-default' : 'cursor-pointer border'
              ]" 
              class="w-9 h-9 rounded-lg flex items-center justify-center font-bold text-sm transition-all"
            >
              {{ page }}
            </button>
          </div>
          
          <button 
            @click="currentPage < totalPages ? currentPage++ : null" 
            :disabled="currentPage === totalPages" 
            class="text-sm font-medium text-blue-600 hover:text-blue-800 disabled:opacity-30 disabled:cursor-not-allowed transition-colors"
          >
            Next
          </button>
        </div>
        
        <div class="flex items-center gap-2 border border-slate-200 rounded-lg px-3 py-1.5 bg-white group hover:border-blue-400 transition-all">
          <select v-model="itemsPerPage" class="text-sm font-medium text-slate-700 bg-transparent outline-none cursor-pointer">
            <option :value="8">8 / page</option>
            <option :value="16">16 / page</option>
            <option :value="24">24 / page</option>
          </select>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed, watch } from 'vue'
import { useRouter } from 'vue-router'
import axios from 'axios'

const router = useRouter()

// State
const allCompanies = ref([])
const searchQuery = ref('')
const currentPage = ref(1)
const itemsPerPage = ref(8)
const loading = ref(true)
const error = ref(null)

// Fetch companies on mount
onMounted(async () => {
  await fetchCompanies()
})

// Fetch all companies
const fetchCompanies = async () => {
  loading.value = true
  error.value = null
  
  try {
    const response = await axios.get('http://localhost:1337/api/companies')
    allCompanies.value = response.data.data || response.data || []
    console.log('Companies loaded:', allCompanies.value)
  } catch (err) {
    console.error('Error fetching companies:', err)
    error.value = 'Failed to load companies. Please try again.'
  } finally {
    loading.value = false
  }
}

// Navigate to company detail - SIMPLE like job page
const goToDetail = (company) => {
  router.push(`/company-detail?id=${company.documentId}`)
}

// Computed properties
const filteredCompanies = computed(() => {
  if (!searchQuery.value) return allCompanies.value
  
  return allCompanies.value.filter(company => 
    company.name?.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})

const totalPages = computed(() => 
  Math.ceil(filteredCompanies.value.length / itemsPerPage.value)
)

const paginatedCompanies = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage.value
  return filteredCompanies.value.slice(start, start + itemsPerPage.value)
})

const visiblePages = computed(() => {
  const total = totalPages.value
  if (total <= 7) return Array.from({ length: total }, (_, i) => i + 1)
  
  const current = currentPage.value
  if (current <= 4) return [1, 2, 3, 4, 5, '...', total]
  if (current >= total - 3) return [1, '...', total - 4, total - 3, total - 2, total - 1, total]
  return [1, '...', current - 1, current, current + 1, '...', total]
})

// Watch for search and items per page changes
watch([searchQuery, itemsPerPage], () => {
  currentPage.value = 1
})
</script>