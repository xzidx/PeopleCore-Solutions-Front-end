<template>
  <div v-if="jobDetail" class="min-h-screen bg-slate-50 p-4 md:p-12 font-sans text-slate-900 flex justify-center items-center mt-[100px]">
    <div class="max-w-8xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-8">
      
      <aside class="lg:col-span-3 space-y-6">
        <button class="w-full bg-blue-500 text-white py-4 px-6 rounded-xl font-semibold shadow-lg shadow-slate-200 text-left hover:bg-slate-800 transition-colors">
          All Job(s)
        </button>

        <div class="bg-slate-100 rounded-3xl p-8 relative overflow-hidden group">
          <div class="relative z-10">
            <p class="text-slate-500 font-medium mb-2">Still Confused?</p>
            <h3 class="text-3xl font-bold mb-8 leading-tight">Ask Us<br/>Anything</h3>
            <button class="bg-blue-700 text-white px-8 py-3 rounded-xl font-bold hover:scale-105 transition-transform">
              Ask us Now
            </button>
          </div>
        </div>
      </aside>

      <main class="lg:col-span-9 space-y-6">
        <section class="bg-white rounded-[2rem] p-8 shadow-sm border border-slate-100">
          <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-6">
            <div class="flex gap-6 items-center">
              <div class="w-24 h-24 border border-slate-100 rounded-2xl flex items-center justify-center p-4">
                <img src="https://upload.wikimedia.org/wikipedia/commons/4/44/Marriott_Logo.svg" alt="Marriott" class="w-full h-auto" />
              </div>
              <div>
                <h1 class="text-2xl font-bold text-slate-800">Marriott Group</h1>
                <p class="text-slate-500">Los Angeles, CA</p>
              </div>
            </div>
          </div>
        </section>

        <section class="bg-white rounded-[2rem] p-10 shadow-sm border border-slate-100">
          <div class="flex justify-between items-start mb-8">
            <div>
              <h2 class="text-3xl font-bold text-slate-800 mb-2">
                {{ jobDetail[0]?.attributes?.title || jobDetail[0]?.title }}
              </h2>
              <p class="text-slate-500 font-medium">Marriott Group <span class="mx-2">•</span> Los Angeles, CA</p>
            </div>
            <div class="text-right">
              <div class="flex items-center gap-6">
                <button class="bg-blue-500 text-white px-10 py-3 rounded-2xl font-bold shadow-lg shadow-blue-200 hover:bg-blue-600 transition-all">
                  Apply Now
                </button>
              </div>
            </div>
          </div>

          <div class="space-y-10">
            <div>
              <h3 class="text-lg font-bold text-slate-800 mb-4">About The Job</h3>
              <p class="text-slate-600 leading-relaxed">
                {{ jobDetail[0]?.attributes?.description || 'No description provided.' }}
              </p>
            </div>
          </div>
        </section>
      </main>
    </div>
  </div>

  <div v-else class="min-h-screen flex items-center justify-center">
    <p class="text-xl font-bold text-slate-400">Loading Job Details...</p>
  </div>
</template> 

<script setup>
  import { ref, onMounted } from 'vue'
  import axios from 'axios'

  // 1. Initialize as null so v-if can track it
  const jobDetail = ref(null)

  const key = {
    headers: {
      Authorization: 'Bearer e10ef327e881d9bd1ed50870ef36e6228d94fb67c5db82824c1e6aea1d3462c9b1a82a539e637dae712a632fa0d035747d726bebc9ebbd73fa1d1539b44c4b02ca143978bd2a852e0241f9e799e82b6b9e614cd09277766e0aa670bfbdc1ab20b02b471655c5798976816eeb27aea59899f236807db38adc1ae0d85edeaa1cce'
    }
  }

  // 2. Fetch data in onMounted to ensure clean reactivity
  onMounted(async () => {
    try {
      const response = await axios.get("http://localhost:1337/api/jobs?populate=*", key)
      jobDetail.value = response.data.data
      console.log("Data loaded:", jobDetail.value)
    } catch (error) {
      console.error("Failed to fetch data:", error)
    }
  })
</script>