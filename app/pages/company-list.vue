<template>
  <div class="min-h-screen bg-[#F8F9FB] p-6 md:p-12 font-sans flex justify-center items-center mt-[50px]">
    <div class=" w-[90%]  h-auto mx-auto">
      
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
          <span class="absolute left-4 top-1/2 -translate-y-1/2 text-slate-400"><i class="fa-solid fa-magnifying-glass"></i></span>
        </div>
      </header>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
        <div 
          v-for="company in paginatedCompanies" 
          :key="company.id"
          @click="goToDetail(company)"
          class="group bg-white rounded-[2.5rem] p-8 border border-slate-100 shadow-sm hover:shadow-xl hover:shadow-indigo-900/5 hover:-translate-y-1 transition-all duration-300 cursor-pointer"
        >
          <div class="flex justify-between items-start mb-6">
            <div class="w-16 h-16 bg-slate-50 rounded-2xl flex items-center justify-center p-3 border border-slate-100 group-hover:border-indigo-100 transition-colors">
              <img :src="company.logo" :alt="company.name" class="w-full h-auto object-contain" />
            </div>
            <span class="bg-blue-500 text-white text-[10px] font-black uppercase px-2 py-1 rounded-md">
              {{ company.openJobs }} Jobs
            </span>
          </div>
          <div class="space-y-1">
            <h2 class="text-xl font-bold text-slate-800 group-hover:text-blue-500 transition-colors">{{ company.name }}</h2>
            <p class="text-sm text-slate-400 flex items-center gap-1">📍 {{ company.location }}</p>
          </div>
          <p class="mt-4 text-sm text-slate-500 line-clamp-2 leading-relaxed">{{ company.description }}</p>
          <div class="flex flex-wrap gap-2 mt-6">
            <span v-for="tag in company.tags" :key="tag" class="px-3 py-1 bg-slate-100 text-slate-500 text-[10px] font-bold rounded-lg">{{ tag }}</span>
          </div>
        </div>
      </div>

      <div v-if="totalPages > 0" class="mt-16 flex flex-wrap items-center justify-center gap-6 bg-white p-4 rounded-2xl shadow-sm border border-slate-100">
        <div class="flex items-center gap-4">
          <button @click="currentPage > 1 ? currentPage-- : null" :disabled="currentPage === 1" class="text-sm font-medium text-slate-400 hover:text-slate-900 disabled:opacity-30 disabled:cursor-not-allowed transition-colors">Previous</button>
          <div class="flex items-center gap-1">
            <button v-for="page in visiblePages" :key="page" @click="typeof page === 'number' ? currentPage = page : null" :class="[currentPage === page ? 'border-blue-500 text-blue-600 ring-1 ring-blue-500' : 'border-transparent text-slate-600 hover:bg-slate-50', page === '...' ? 'cursor-default' : 'cursor-pointer border']" class="w-9 h-9 rounded-lg flex items-center justify-center font-bold text-sm transition-all">{{ page }}</button>
          </div>
          <button @click="currentPage < totalPages ? currentPage++ : null" :disabled="currentPage === totalPages" class="text-sm font-medium text-blue-600 hover:text-blue-800 disabled:opacity-30 disabled:cursor-not-allowed transition-colors">Next</button>
        </div>
        <div class="flex items-center gap-2 border border-slate-200 rounded-lg px-3 py-1.5 bg-white group hover:border-blue-400 transition-all">
          <select v-model="itemsPerPage" class="text-sm font-medium text-slate-700 bg-transparent outline-none cursor-pointer">
            <option :value="8">8 / page</option>
            <option :value="16">16 / page</option>
          </select>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const searchQuery = ref('')
const currentPage = ref(1)
const itemsPerPage = ref(8)

const allCompanies = [
  { id: 1, name: 'Marriott Group', location: 'Los Angeles, CA', logo: 'https://upload.wikimedia.org/wikipedia/commons/4/44/Marriott_Logo.svg', description: 'Global hospitality leader providing world-class travel experiences.', openJobs: 12, tags: ['Hospitality', 'Travel'] },
  { id: 2, name: 'PeopleCore', location: 'Phnom Penh, KH', logo: 'https://img.logoipsum.com/296.svg', description: 'Specializing in connecting top-tier talent with innovative tech startups.', openJobs: 5, tags: ['Recruitment', 'HR'] },
  { id: 3, name: 'DesignFlow', location: 'San Francisco, CA', logo: 'https://img.logoipsum.com/285.svg', description: 'A creative agency pushing the boundaries of digital product design.', openJobs: 3, tags: ['Design', 'Agency'] },
  { id: 4, name: 'TechStack', location: 'Austin, TX', logo: 'https://img.logoipsum.com/225.svg', description: 'Building the next generation of scalable cloud infrastructure.', openJobs: 24, tags: ['SaaS', 'Cloud'] },
  { id: 5, name: 'Velocity AI', location: 'Seattle, WA', logo: 'https://img.logoipsum.com/255.svg', description: 'Accelerating machine learning workflows for enterprise level data.', openJobs: 18, tags: ['AI', 'Data'] },
  { id: 6, name: 'GreenLeaf', location: 'Portland, OR', logo: 'https://img.logoipsum.com/284.svg', description: 'Sustainable solutions for modern urban agriculture and living.', openJobs: 7, tags: ['Eco', 'AgriTech'] },
  { id: 7, name: 'FinPort', location: 'London, UK', logo: 'https://img.logoipsum.com/218.svg', description: 'Simplifying global payments with secure, transparent fintech tools.', openJobs: 14, tags: ['Fintech', 'Finance'] },
  { id: 8, name: 'HealthSync', location: 'Boston, MA', logo: 'https://img.logoipsum.com/258.svg', description: 'Bridging the gap between patients and providers through telemedicine.', openJobs: 9, tags: ['Health', 'App'] },
  { id: 9, name: 'Nova Stream', location: 'Toronto, ON', logo: 'https://img.logoipsum.com/211.svg', description: 'High-performance streaming services for the modern gaming era.', openJobs: 21, tags: ['Gaming', 'Media'] },
  { id: 10, name: 'Urban Code', location: 'Berlin, DE', logo: 'https://img.logoipsum.com/297.svg', description: 'Crafting elegant software for smart city management and transit.', openJobs: 4, tags: ['Software', 'City'] },
  { id: 11, name: 'SecureNode', location: 'Singapore, SG', logo: 'https://img.logoipsum.com/221.svg', description: 'Advanced cybersecurity protecting decentralized networks worldwide.', openJobs: 11, tags: ['Security', 'Web3'] },
  { id: 12, name: 'SkyBound', location: 'Denver, CO', logo: 'https://img.logoipsum.com/233.svg', description: 'Leading the way in aerospace engineering and private space flight.', openJobs: 32, tags: ['Aerospace', 'Tech'] },
  { id: 13, name: 'Pure Water', location: 'Sydney, AU', logo: 'https://img.logoipsum.com/217.svg', description: 'Innovation in water filtration and global conservation efforts.', openJobs: 6, tags: ['Conservation', 'Water'] },
  { id: 14, name: 'EduPulse', location: 'Mumbai, IN', logo: 'https://img.logoipsum.com/259.svg', description: 'Interactive learning platforms for primary and secondary education.', openJobs: 15, tags: ['EdTech', 'Education'] },
  { id: 15, name: 'AutoVision', location: 'Tokyo, JP', logo: 'https://img.logoipsum.com/243.svg', description: 'Developing autonomous vehicle systems for safer public roads.', openJobs: 27, tags: ['Auto', 'AI'] },
  { id: 16, name: 'Cortex Design', location: 'Montreal, QC', logo: 'https://img.logoipsum.com/288.svg', description: 'Industrial design firm focused on ergonomic workplace hardware.', openJobs: 8, tags: ['Industrial', 'Design'] },
]

const goToDetail = (company) => {
  router.push({
    name: 'company-detail',
    params: { id: company.id },
    state: { company } 
  })
}

const filteredCompanies = computed(() => allCompanies.filter(c => c.name.toLowerCase().includes(searchQuery.value.toLowerCase())))
const totalPages = computed(() => Math.ceil(filteredCompanies.value.length / itemsPerPage.value))
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
watch([searchQuery, itemsPerPage], () => { currentPage.value = 1 })
</script>