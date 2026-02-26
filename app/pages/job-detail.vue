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
          <div class="mt-8 flex justify-center">
            
          </div>
        </div>
      </aside>

      <main class="lg:col-span-9 space-y-6">
        <button class="flex items-center gap-2 text-slate-400 hover:text-slate-600 font-medium transition-colors mb-2">
         
        </button>

        <section class="bg-white rounded-[2rem] p-8 shadow-sm border border-slate-100">
          <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-6">
            <div class="flex gap-6 items-center">
              <div class="w-24 h-24 border border-slate-100 rounded-2xl flex items-center justify-center p-4">
                <img src="https://upload.wikimedia.org/wikipedia/commons/4/44/Marriott_Logo.svg" alt="Marriott" class="w-full h-auto" />
              </div>
              <div>
                <h1 class="text-2xl font-bold text-slate-800">{{ jobDetail[0]?.title }}</h1>
                <p class="text-slate-500">Los Angeles, CA</p>
                <div class="flex gap-2 mt-3">
                  <span class="px-3 py-1 bg-indigo-50 text-indigo-600 text-xs font-bold rounded-lg">Logistics</span>
                  <span class="px-3 py-1 bg-purple-50 text-purple-600 text-xs font-bold rounded-lg">Hospitality</span>
                </div>
              </div>
            </div>
            
            <div class="flex flex-col md:items-end gap-4">
              <div class="flex gap-8 text-sm">
                <div class="text-center">
                  <p class="text-slate-400 font-medium">Type</p>
                  <p class="font-bold">{{ jobDetail[0]?.schedule }} </p>
                </div>
                <div class="text-center border-l border-slate-100 pl-8">
                  <p class="text-slate-400 font-medium">Company Size</p>
                  <p class="font-bold">200 - 500 employee(s)</p>
                </div>
              </div>
              <button class="text-blue-600 font-bold border border-blue-600 px-6 py-2 rounded-xl hover:bg-blue-500 transition-colors">
                View Company Page
              </button>
            </div>
          </div>
        </section>

        <section class="bg-white rounded-[2rem] p-10 shadow-sm border border-slate-100">
          <div class="flex justify-between items-start mb-8">
            <div>
              <h2 class="text-3xl font-bold text-slate-800 mb-2"></h2>
              <p class="text-slate-500 font-medium">{{ jobDetail[0]?.title }} <span class="mx-2">•</span> {{ jobDetail[0]?.location }}</p>
              <p class="text-sm mt-2 font-bold uppercase tracking-wider text-slate-400">Salary <span class="text-slate-800 text-lg">{{ jobDetail[0]?.salary  }} $/Month</span></p>
            </div>
            <div class="text-right">
              <p class="text-xs text-slate-400 mb-4 font-medium uppercase tracking-widest">Posted: 03 hours(s) ago</p>
              <div class="flex items-center gap-6">
                <button class="text-slate-500 font-bold underline hover:text-slate-800">Save Job</button>
                <button class="bg-blue-500 text-white px-10 py-3 rounded-2xl font-bold shadow-lg shadow-blue-200 hover:bg-blue-600 hover:scale-[1.02] transition-all">
                  Apply Now
                </button>
              </div>
            </div>
          </div>

          <div class="space-y-10">
            <div>
              <h3 class="text-lg font-bold text-slate-800 mb-4">Minimum Qualifications</h3>
              <ul class="list-disc list-inside space-y-2 text-slate-600 leading-relaxed">
                <li>Bachelor's degree or equivalent practical experience.</li>
                <li>6 years of experience in an advertising sales, business development, and/or online media environment.</li>
              </ul>
            </div>

            <div>
              <h3 class="text-lg font-bold text-slate-800 mb-4">Preferred Qualifications</h3>
              <div class="space-y-4 text-slate-600 leading-relaxed">
                <p>Experience working in sales, consulting, media, or advertising.</p>
                <p>Experience in relationship and stakeholder management.</p>
                <p>Ability to effectively analyze spreadsheets and create/deliver impactful presentations.</p>
                <p>Excellent communication and influencing skills, and ability to present advertising solutions to multiple audiences.</p>
              </div>
            </div>

            <div>
              <h3 class="text-lg font-bold text-slate-800 mb-4">About The Job</h3>
              <p class="text-slate-600 leading-relaxed">
                Businesses that partner with Google come in all shapes, sizes and market caps, and no one Google advertising solution works for all. Your knowledge of online media combined with your communication skills and analytical abilities shapes how new and existing business grow.
              </p>
            </div>
          </div>
        </section>
      </main>
    </div>
  </div>
</template> 

<script setup>
  import { ref, onMounted } from 'vue'
  import axios from 'axios'

  // Create a reactive reference for the jobs
  const jobDetail = ref([])

  const key = {
    headers: {
      Authorization: 'Bearer e10ef327e881d9bd1ed50870ef36e6228d94fb67c5db82824c1e6aea1d3462c9b1a82a539e637dae712a632fa0d035747d726bebc9ebbd73fa1d1539b44c4b02ca143978bd2a852e0241f9e799e82b6b9e614cd09277766e0aa670bfbdc1ab20b02b471655c5798976816eeb27aea59899f236807db38adc1ae0d85edeaa1cce'
    }
  }

  onMounted(async () => {
    try {
      const response = await axios.get("http://localhost:1337/api/jobs", key)
      // Strapi data is usually in response.data.data
      jobDetail.value = response.data.data
    } catch (error) {
      console.error("Error fetching jobs:", error)
    }
  })
</script>