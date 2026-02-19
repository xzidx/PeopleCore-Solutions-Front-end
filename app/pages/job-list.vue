<template>
  <div class="bg-white w-[100%] bg-black mt-[100px]">
    <div class="flex flex-wrap items-center bg-white p-1 rounded-xl border border-gray-200 shadow-sm w-full max-w-[1400px] mx-auto font-sans relative">
      <div class="flex flex-1 items-center gap-2 px-4 min-h-[56px] min-w-[300px]">
        <svg class="w-5 h-5 text-gray-400 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
        </svg>
        <div class="flex flex-wrap gap-2">
          <input 
            v-model="searchQuery"
            type="text" 
            placeholder="Add more..." 
            class="outline-none text-sm text-gray-500 bg-transparent flex-1 min-w-[50px]" 
          />
        </div>
        <div class="h-8 w-[1px] bg-gray-200 ml-auto hidden md:block"></div>
      </div>

      <div v-for="(dropdown, index) in dropdownConfigs" :key="index" class="relative group">
        <div @click="toggleDropdown(dropdown.key)" class="flex items-center gap-2 px-6 border-r border-gray-100 h-14 cursor-pointer hover:bg-gray-50 transition-colors">
          <svg v-html="dropdown.icon" class="w-5 h-5 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"></svg>
          <span class="text-sm font-medium whitespace-nowrap" :class="selections[dropdown.key] ? 'text-gray-900' : 'text-gray-500'">
            {{ selections[dropdown.key] || dropdown.label }}
          </span>
          <svg class="w-4 h-4 text-gray-400 transition-transform" :class="{'rotate-180': openDropdown === dropdown.key}" fill="currentColor" viewBox="0 0 20 20">
            <path d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"/>
          </svg>
        </div>

        <div v-if="openDropdown === dropdown.key" class="absolute top-full left-0 w-64 bg-white border border-gray-200 rounded-xl shadow-xl z-50 mt-2 py-2 max-h-60 overflow-y-auto">
          <button v-for="option in dropdown.options" :key="option" @click="selectOption(dropdown.key, option)" class="w-full text-left px-4 py-2.5 text-sm hover:bg-blue-50 hover:text-blue-600 transition-colors">
            {{ option }}
          </button>
        </div>
      </div>

      <button class="bg-blue-500 text-white px-8 h-12 rounded-lg text-sm font-bold tracking-tight hover:bg-gray-800 transition-all uppercase m-1 ml-4">
        Start Searching
      </button>
    </div>

    <div class="bg-white w-[100%] p-8">
      <div class="max-w-8xl mx-auto flex gap-8">
        <aside class="w-64 shrink-0 hidden lg:block">
          <h2 class="text-xl font-bold mb-6">Filters</h2>
          
          <div class="mb-8">
            <p class="text-gray-400 text-sm font-bold uppercase mb-4 tracking-wider">Type of Employment</p>
            <div class="space-y-3">
              <label v-for="item in scheduleOptions" :key="item" class="flex items-center gap-3 cursor-pointer group">
                <input type="checkbox" class="w-5 h-5 rounded accent-black cursor-pointer border-gray-300">
                <span class="text-gray-700 font-medium text-sm group-hover:text-blue-500 transition-colors">{{ item }}</span>
              </label>
            </div>
          </div>

          <div class="mb-8">
              <p class="text-gray-400 text-sm font-bold uppercase mb-4 tracking-wider">Employment type</p>
              <div class="space-y-3">
                  <label v-for="item in employmentType" :key="item" class="flex items-center gap-3 cursor-pointer group">
                  <input type="checkbox" class="w-5 h-5 rounded accent-black cursor-pointer border-gray-300">
                  <span class="text-gray-700 font-medium text-sm group-hover:text-blue-500 transition-colors">{{ item }}</span>
                  </label>
              </div>
          </div>

          <div class="mb-8">
            <p class="text-gray-400 text-sm font-bold uppercase mb-4 tracking-wider">Seniority Level</p>
            <div class="space-y-3">
                <label v-for="level in senioritylevel" :key="level" class="flex items-center gap-3 cursor-pointer group">
                <input type="checkbox" class="w-5 h-5 rounded accent-black cursor-pointer border-gray-300">
                <span class="text-gray-700 font-medium text-sm group-hover:text-blue-500 transition-colors">{{ level }}</span>
                </label>
            </div>
          </div>
        </aside>

        <main class="flex-1">
          <div class="flex justify-between items-center mb-8">
            <h1 class="text-3xl font-bold">Recommended jobs <span class="bg-white border text-sm px-3 py-1 rounded-full ml-2">{{ filteredJobs.length }}</span></h1>
            <div class="text-sm text-gray-500 font-medium cursor-pointer">
              Sort by: <span class="text-black font-bold">Last updated <i class="fa-solid fa-sliders ml-1"></i></span>
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-6">
            <NuxtLink v-for="(job, index) in paginatedJobs" :key="index" :to="`/job-detail?id=${job.id}`">
               <JobCard v-bind="job" class="cursor-pointer transition-transform hover:scale-[1.01]" />
            </NuxtLink>
          </div>
        </main>
      </div>
    </div>

    <div v-if="totalPages > 0" class="mt-1 flex flex-wrap items-center justify-center gap-6 bg-white p-4 rounded-2xl shadow-sm border border-slate-100">
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
                currentPage === page 
                  ? 'border-blue-500 text-blue-600 ring-1 ring-blue-500' 
                  : 'border-transparent text-slate-600 hover:bg-slate-50',
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
          <select 
            v-model="itemsPerPage" 
            class="text-sm font-medium text-slate-700 bg-transparent outline-none cursor-pointer"
          >
            <option :value="3">3 / page</option>
            <option :value="6">6 / page</option>
            <option :value="12">12 / page</option>
          </select>
        </div>
      </div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'

// --- UI State ---
const openDropdown = ref(null)
const searchQuery = ref('')
const currentPage = ref(1)
const itemsPerPage = ref(6)

const selections = ref({
  location: '',
  jobType: '',
  salary: ''
})

// --- Interaction Logic ---
const toggleDropdown = (key) => {
  openDropdown.value = openDropdown.value === key ? null : key
}

const selectOption = (key, value) => {
  selections.value[key] = value
  openDropdown.value = null
}

// --- Filter Data ---
const scheduleOptions = ['Full time', 'Part time', 'Internship', 'Project work', 'Volunteering']
const employmentType = ['Full day', 'Flexible schedule', 'Shift work', 'Distant work', 'Shift method']
const senioritylevel = ['Student', 'Junior', 'Middle', 'Senior', 'Lead']

const dropdownConfigs = [
  {
    key: 'location',
    label: 'All Countries',
    icon: '<path d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" /><path d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />',
    options: ['United States', 'United Kingdom', 'Canada', 'Remote']
  },
  {
    key: 'jobType',
    label: 'Job Type',
    icon: '<path d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />',
    options: ['Full-time', 'Part-time', 'Contract', 'Freelance']
  },
  {
    key: 'salary',
    label: 'Salary Range',
    icon: '<path d="M3 10h18M7 15h1m4 0h1m-7 4h12a2 2 0 002-2V5a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />',
    options: ['$0 - $1k', '$1k - $5k', '$10k+']
  }
]

// --- Job Data (ADDED IDs) ---
const jobs = ref([
  { id: 1, date: '12 Mar, 2026', company: 'Spotify', title: 'Product Designer', tags: ['Full time', 'Senior level'], price: 320, location: 'Stockholm, SE', bgColor: 'bg-[#E7DBFF]' },
  { id: 2, date: '05 Apr, 2026', company: 'Slack', title: 'Frontend Engineer', tags: ['Distant', 'Middle level'], price: 280, location: 'Remote', bgColor: 'bg-[#D1F7EA]' },
  { id: 3, date: '22 Jan, 2026', company: 'Airbnb', title: 'UX Researcher', tags: ['Project work', 'Senior level'], price: 400, location: 'San Francisco, CA', bgColor: 'bg-[#FFE2C5]' },
  { id: 4, date: '18 Feb, 2026', company: 'Tesla', title: 'Fullstack Developer', tags: ['Full time', 'Lead level'], price: 450, location: 'Austin, TX', bgColor: 'bg-[#D1F7EA]' },
  { id: 5, date: '01 May, 2026', company: 'Netflix', title: 'Content Strategist', tags: ['Part time', 'Junior level'], price: 190, location: 'Los Angeles, CA', bgColor: 'bg-[#E7DBFF]' },
  { id: 6, date: '14 Mar, 2026', company: 'Adobe', title: 'Creative Director', tags: ['Full Day', 'Senior level'], price: 550, location: 'San Jose, CA', bgColor: 'bg-[#FFE2C5]' },
  { id: 7, date: '30 Apr, 2026', company: 'Figma', title: 'Design Systems Lead', tags: ['Distant', 'Lead level'], price: 420, location: 'Remote', bgColor: 'bg-[#D1F7EA]' },
  { id: 8, date: '10 Feb, 2026', company: 'Microsoft', title: 'Azure Specialist', tags: ['Shift work', 'Middle level'], price: 310, location: 'Seattle, WA', bgColor: 'bg-[#FFE2C5]' },
  { id: 9, date: '25 Mar, 2026', company: 'Shopify', title: 'E-commerce Expert', tags: ['Contract', 'Senior level'], price: 290, location: 'Ottawa, ON', bgColor: 'bg-[#E7DBFF]' },
  { id: 10, date: '08 May, 2026', company: 'Apple', title: 'iOS Developer', tags: ['Full time', 'Senior level'], price: 480, location: 'Cupertino, CA', bgColor: 'bg-[#D1F7EA]' },
  { id: 11, date: '19 Jan, 2026', company: 'Notion', title: 'Customer Success', tags: ['Flexible', 'Junior level'], price: 120, location: 'New York, NY', bgColor: 'bg-[#FFE2C5]' },
  { id: 12, date: '02 Mar, 2026', company: 'Zoom', title: 'Security Engineer', tags: ['Distant', 'Middle level'], price: 340, location: 'Remote', bgColor: 'bg-[#E7DBFF]' },
  { id: 13, date: '15 Feb, 2026', company: 'Discord', title: 'Community Manager', tags: ['Part time', 'Middle level'], price: 210, location: 'Remote', bgColor: 'bg-[#D1F7EA]' },
  { id: 14, date: '28 Feb, 2026', company: 'Reddit', title: 'Backend Engineer', tags: ['Full time', 'Senior level'], price: 390, location: 'San Francisco, CA', bgColor: 'bg-[#FFE2C5]' },
  { id: 15, date: '10 Apr, 2026', company: 'Stripe', title: 'Payment Architect', tags: ['Full Day', 'Lead level'], price: 510, location: 'Dublin, IE', bgColor: 'bg-[#E7DBFF]' },
  { id: 16, date: '05 May, 2026', company: 'HubSpot', title: 'Marketing Lead', tags: ['Flexible', 'Senior level'], price: 275, location: 'Boston, MA', bgColor: 'bg-[#D1F7EA]' },
  { id: 17, date: '12 Mar, 2026', company: 'Spotify', title: 'Product Designer', tags: ['Full time', 'Senior level'], price: 320, location: 'Stockholm, SE', bgColor: 'bg-[#E7DBFF]' },
  { id: 18, date: '05 Apr, 2026', company: 'Slack', title: 'Frontend Engineer', tags: ['Distant', 'Middle level'], price: 280, location: 'Remote', bgColor: 'bg-[#D1F7EA]' },
])

// --- Search & Pagination Logic ---
const filteredJobs = computed(() => {
  return jobs.value.filter(job => 
    job.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
    job.company.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})

const totalPages = computed(() => Math.ceil(filteredJobs.value.length / itemsPerPage.value))

const paginatedJobs = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage.value
  return filteredJobs.value.slice(start, start + itemsPerPage.value)
})

const visiblePages = computed(() => {
  const total = totalPages.value
  if (total <= 7) return Array.from({ length: total }, (_, i) => i + 1)
  const current = currentPage.value
  if (current <= 4) return [1, 2, 3, 4, 5, '...', total]
  if (current >= total - 3) return [1, '...', total - 4, total - 3, total - 2, total - 1, total]
  return [1, '...', current - 1, current, current + 1, '...', total]
})

watch([searchQuery, itemsPerPage], () => { currentPage.value = 1 })
</script>