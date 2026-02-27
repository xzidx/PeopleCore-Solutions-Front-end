<template>
  <div class="min-h-screen bg-[#F8F9FB] pb-24 font-sans text-slate-900 mt-[20px]">
    <div class="h-64 bg-blue-500 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-r from-blue-900/40 to-indigo-900/40"></div>
    </div>

    <div class="max-w-7xl mx-auto px-6 md:px-12 -mt-24 relative z-10">
      
      <!-- Loading State -->
      <div v-if="loading" class="text-center py-40 bg-white rounded-[4rem] border border-slate-100 shadow-sm">
        <div class="animate-spin text-blue-600 text-5xl mb-6"><i class="fa-solid fa-circle-notch"></i></div>
        <p class="text-slate-400 font-black uppercase tracking-[0.3em] text-xs">Loading Company Data...</p>
      </div>

      <!-- Company Data -->
      <div v-else-if="company" class="grid grid-cols-1 lg:grid-cols-12 gap-10">
        
        <div class="lg:col-span-8 space-y-8">
          
          <div class="bg-white rounded-xl p-10 md:p-14 shadow-xl shadow-slate-200/50 border border-white">
            <div class="flex flex-col md:flex-row items-center md:items-start gap-10">
              <div class="w-32 h-32 md:w-40 md:h-40 bg-white rounded-md flex items-center justify-center p-8 shadow-2xl shadow-blue-900/10 border border-slate-50 shrink-0">
                <img :src="company.logo" :alt="company.name" class="w-full h-auto object-contain" />
              </div>
              <div class="flex-1 text-center md:text-left space-y-4">
                <div class="flex flex-wrap justify-center md:justify-start items-center gap-3">
                  <h1 class="text-5xl md:text-6xl font-black tracking-tighter text-slate-900">{{ company.title }}</h1>
                  <span class="bg-blue-500 text-white text-[10px] font-black px-3 py-1 rounded-md uppercase tracking-widest">Hiring</span>
                </div>
                <div class="flex flex-wrap justify-center md:justify-start gap-6 text-slate-400 font-medium">
                  <span class="flex items-center gap-2"><i class="fa-solid fa-location-dot text-blue-500"></i> {{ company.location }}</span>
                  <span class="flex items-center gap-2"><i class="fa-solid fa-users text-blue-500"></i> {{ company.Employees }}</span>
                </div>
              </div>
            </div>
          </div>

          <section class="bg-white rounded-xl p-10 border border-slate-100 shadow-sm">
            <h3 class="text-2xl font-black mb-6 flex items-center gap-3">
              <span class="w-2.5 h-8 bg-blue-500 rounded-xl"></span>
              Our Story
            </h3>
            <p class="text-slate-500 leading-relaxed text-lg mb-10">
              {{ company.description }}
            </p>
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
              <div v-for="tag in company.tags" :key="tag" class="bg-slate-50 p-5 rounded-xl text-center border border-slate-100">
                <p class="text-[10px] font-black text-slate-400 uppercase mb-1 tracking-widest">Expertise</p>
                <p class="font-bold text-slate-800">{{ tag }}</p>
              </div>
            </div>
          </section>

          <section class="bg-white rounded-xl p-10 border border-slate-100 shadow-sm">
            <h3 class="text-2xl font-black mb-8 tracking-tight">Working Culture</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-x-12 gap-y-8">
              <div v-for="stat in cultureStats" :key="stat.label" class="space-y-3">
                <div class="flex justify-between text-[15px] font-black ">
                  <span class="text-slate-400">{{ stat.label }}</span>
                  <span class="text-blue-600">{{ stat.value }}%</span>
                </div>
                <div class="h-2.5 bg-slate-100 rounded-full overflow-hidden">
                  <div class="h-full bg-blue-500 rounded-full" :style="{ width: stat.value + '%' }"></div>
                </div>
              </div>
            </div>
          </section>

          <section class="bg-white rounded-sm p-10 border border-slate-100 shadow-sm">
            <h3 class="text-2xl font-black mb-10">Company Benefits</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
              <div v-for="benefit in benefits" :key="benefit.title" class="flex gap-5">
                <div class="w-14 h-14 shrink-0 bg-blue-50 rounded-sm flex items-center justify-center text-blue-600 text-xl">
                  <i :class="benefit.icon"></i>
                </div>
                <div>
                  <h4 class="font-black text-slate-800 leading-tight">{{ benefit.title }}</h4>
                  <p class="text-sm text-slate-500 mt-1">{{ benefit.desc }}</p>
                </div>
              </div>
            </div>
          </section>
        </div>

        <div class="lg:col-span-4 space-y-8">
          
          <div class="bg-blue-500 rounded-xl p-10 text-white shadow-2xl shadow-blue-900/30">
            <h4 class="text-xl font-bold mb-8">Join the Team</h4>
            <div class="space-y-6 mb-10">
              <div class="flex justify-between items-center border-b border-white/10 pb-5">
                <span class="text-white">Open Jobs</span>
                <span class="font-black text-3xl text-white">{{ company.openJobs }}</span>
              </div>
              <div class="flex justify-between items-center border-b border-white/10 pb-5">
                <span class="text-white">Avg.Salary</span>
                <span class="font-bold text-lg text-white">${{ company.Salary }}</span>
              </div>
            </div>
            <button class="w-full bg-blue-600 text-white py-5 rounded-2xl font-black uppercase tracking-widest text-xs hover:bg-white hover:text-slate-900 transition-all">
              View All Openings
            </button>
          </div>

          <div class="bg-white rounded-xl p-8 border border-slate-100 shadow-sm">
            <h4 class="font-black text-slate-900 mb-6 px-2">Community</h4>
            <div class="flex gap-3">
              <a href="#" class="w-full aspect-square max-w-[60px] rounded-2xl bg-slate-50 flex items-center justify-center text-slate-400 hover:text-blue-600 transition-all border border-slate-100"><i class="fa-brands fa-linkedin-in text-xl"></i></a>
              <a href="#" class="w-full aspect-square max-w-[60px] rounded-2xl bg-slate-50 flex items-center justify-center text-slate-400 hover:text-blue-400 transition-all border border-slate-100"><i class="fa-brands fa-twitter text-xl"></i></a>
              <a href="#" class="w-full aspect-square max-w-[60px] rounded-2xl bg-slate-50 flex items-center justify-center text-slate-400 hover:text-pink-500 transition-all border border-slate-100"><i class="fa-brands fa-instagram text-xl"></i></a>
            </div>
          </div>
        </div>

      </div>

      <!-- No Company Found -->
      <div v-else class="text-center py-40 bg-white rounded-[4rem] border border-slate-100 shadow-sm">
        <div class="text-red-500 text-5xl mb-6"><i class="fa-solid fa-building"></i></div>
        <p class="text-slate-400 font-black uppercase tracking-[0.3em] text-xs">Company Not Found</p>
        <button @click="$router.back()" class="mt-4 text-blue-500">Go Back</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue' // 1. Added computed here
import { useRoute, useRouter } from 'vue-router'
import axios from 'axios'

const route = useRoute()
const router = useRouter()
const company = ref(null)
const loading = ref(true)

const cultureStats = computed(() => [
  { 
    label: 'Work-Life Balance', 
    value: company.value?.workLifeScore || 0 
  },
  { 
    label: 'Growth & Learning', 
    value: company.value?.growthScore || 0 
  },
  { 
    label: 'Diversity & Inclusion', 
    value: company.value?.diversityScore || 0 
  },
  { 
    label: 'Remote Flexibility', 
    value: company.value?.remoteScore || 0 
  }
])

const benefits = computed(() => [
  { 
    icon: 'fa-solid fa-laptop-house', 
    title: 'Remote Work', 
    desc: company.value?.remoteDesc || 'Nothing' 
  },
  { 
    icon: 'fa-solid fa-umbrella-beach', 
    title: 'Unlimited PTO', 
    desc: company.value?.ptoDesc || 'Nothing' 
  },
  { 
    icon: 'fa-solid fa-briefcase-medical', 
    title: 'Health First', 
    desc: company.value?.healthDesc || 'Nothing' 
  },
  { 
    icon: 'fa-solid fa-graduation-cap', 
    title: 'Learning Stipend', 
    desc: company.value?.learningDesc || 'Nothing' 
  }
])
onMounted(async () => {
  try {
    const companyDocumentId = route.query.id
    if (!companyDocumentId) {
      loading.value = false
      return
    }
    
    const response = await axios.get('http://localhost:1337/api/companies')
    const companies = response.data.data || response.data
    const foundCompany = companies.find(c => c.documentId === companyDocumentId)
    
    if (foundCompany) {
      company.value = foundCompany
    }
  } catch (error) {
    console.error("Failed to fetch company:", error)
  } finally {
    loading.value = false
  }
})
</script>