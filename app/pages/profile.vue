<template>
  <div class="min-h-screen w-full bg-[#F8F9FB] flex items-center justify-center font-sans text-slate-900 mt-[50px]">

    <div class="w-full max-w-8xl bg-white rounded-[2rem] flex overflow-hidden min-h-[800px] border border-slate-100">

    
      <aside class="w-64 border-r border-slate-50 bg-[#FBFBFC] p-8 hidden lg:flex flex-col shrink-0">

        <div class="flex items-center gap-2 text-slate-400 mb-10 hover:text-indigo-600 cursor-pointer transition-all group">
          <i class="fa-solid fa-chevron-left text-[10px] group-hover:-translate-x-1 transition-transform"></i>
          <span class="text-xl font-bold uppercase tracking-widest">My account</span>
        </div>

        <nav class="space-y-10">

          <div>
            

            <ul class="space-y-2 text-base font-bold">

              
              <li
                @click="activeTab = 'profile'"
                :class="activeTab === 'profile'
                  ? activeClass
                  : inactiveClass"
              >
                <i class="fa-regular fa-user"></i>
                My Profile
              </li>

            
              <li
                @click="activeTab = 'security'"
                :class="activeTab === 'security'
                  ? activeClass
                  : inactiveClass"
              >
                <i class="fa-solid fa-shield-halved"></i>
                Security
              </li>


              <li
                @click="activeTab = 'recruitment'"
                :class="activeTab === 'recruitment'
                  ? activeClass
                  : inactiveClass"
              >
                <i class="fa-solid fa-briefcase"></i>
                Recruitment Admin
              </li>

              <li
                @click="activeTab = 'notifications'"
                :class="activeTab === 'notifications'
                  ? activeClass
                  : inactiveClass"
              >
                <i class="fa-regular fa-bell"></i>
                Notifications
              </li>

              <li
                @click="activeTab = 'candidate'"
                :class="activeTab === 'candidate'
                  ? activeClass
                  : inactiveClass"
              >
                <i class="fa-solid fa-user-group"></i>
                Candidate Notifications
              </li>


            </ul>
          </div>

        </nav>
      </aside>

     
      <main class="flex-1 p-8 md:p-12 lg:p-16 overflow-y-auto">
        <div class="max-w-4xl mx-auto">

         
          <div v-if="activeTab === 'profile'" class="space-y-12">

            <header>
              <h1 class="text-3xl font-black text-slate-900 tracking-tight">
                My Profile
              </h1>
              <p class="text-slate-500 mt-1 font-medium">
                Manage your personal recruiter settings
              </p>
            </header>

         
            <section class="space-y-4">
              <h2 class="text-sm font-bold text-slate-900">
                Your Profile Photo
              </h2>

              <div class="flex flex-wrap items-center gap-10">
                <img
                  src="/../public/images/profile-pic.jpg"
                  class="w-[150px] h-[150px] rounded-3xl object-cover shadow-lg ring-4 ring-white"
                />

                <div class="flex flex-col gap-3">
                  <div class="flex gap-5">
                    <button class="bg-indigo-600 text-white px-6 py-2.5 rounded-xl text-sm font-bold hover:bg-indigo-700 shadow-lg shadow-indigo-100 transition-all">
                      Change Photo
                    </button>

                    <button class="bg-white border border-slate-200 text-red-500 px-4 py-2.5 rounded-xl text-sm font-bold hover:bg-red-50 transition-colors">
                      <i class="fa-regular fa-trash-can"></i>
                    </button>
                  </div>

                  <p class="text-[11px] text-slate-400 font-medium tracking-wide">
                    Recommended: 256x256px. PNG or JPG.
                  </p>
                </div>
              </div>
            </section>

          
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">

              <div class="space-y-2">
                <label class="label">First Name</label>
                <input type="text" value="Julian" class="input-style" />
              </div>

              <div class="space-y-2">
                <label class="label">Last Name</label>
                <input type="text" value="Hernandez" class="input-style" />
              </div>

              <div class="md:col-span-2 space-y-2">
                <label class="label">Email Address</label>
                <input type="email" value="julian.hernandez@recruit.com"
                  disabled
                  class="w-full bg-slate-100 border border-slate-200 rounded-2xl px-5 py-4 text-slate-400 font-bold cursor-not-allowed"
                />
              </div>

              <div class="md:col-span-2 space-y-2">
                <label class="label">Phone Number</label>
                <input type="tel" value="+1 555 012 3456" class="input-style" />
              </div>

            </div>

          </div>

         
          <div v-if="activeTab === 'security'" class="space-y-10">

            <header>
              <h1 class="text-3xl font-black text-slate-900 tracking-tight">
                Security
              </h1>
              <p class="text-slate-500 mt-1 font-medium">
                Manage your password and account security
              </p>
            </header>

            <div class="bg-white border border-slate-100 rounded-3xl p-8 space-y-6">

              <div class="space-y-2">
                <label class="label">Current Password</label>
                <input type="password" class="input-style" />
              </div>

              <div class="space-y-2">
                <label class="label">New Password</label>
                <input type="password" class="input-style" />
              </div>

              <div class="space-y-2">
                <label class="label">Confirm Password</label>
                <input type="password" class="input-style" />
              </div>

              <button class="bg-indigo-600 text-white px-8 py-3 rounded-xl text-sm font-bold hover:bg-indigo-700 shadow-lg shadow-indigo-100 transition-all">
                Update Password
              </button>

            </div>

          </div>
          
          <div v-if="activeTab === 'recruitment'" class="space-y-10">

              <header>
                <h1 class="text-3xl font-black text-slate-900 tracking-tight">
                  Recruitment request
                </h1>
                <p class="text-slate-500 mt-1 font-medium">
                  Control how you receive recruitment activity updates
                </p>
              </header>

              <div class="bg-white border border-slate-100 rounded-3xl p-8 space-y-8">

             
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">New Application</h3>
                    <p class="text-sm text-slate-400">
                      Get notified when a candidate applies to a job.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

               
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">Interview Scheduled</h3>
                    <p class="text-sm text-slate-400">
                      Receive alerts when interviews are booked.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

              
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">Candidate Messages</h3>
                    <p class="text-sm text-slate-400">
                      Be notified when candidates send you messages.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

             
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">Offer Accepted</h3>
                    <p class="text-sm text-slate-400">
                      Get an alert when a candidate accepts an offer.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

              </div>

            </div>

            <div v-if="activeTab === 'notifications'" class="space-y-10">

              <header>
                <h1 class="text-3xl font-black text-slate-900 tracking-tight">
                  Notifications
                </h1>
                <p class="text-slate-500 mt-1 font-medium">
                  Manage how you receive notifications
                </p>
              </header>

              <div class="bg-white border border-slate-100 rounded-3xl p-8 space-y-6">

                <div class="flex items-center justify-between">
                  <span class="font-bold text-slate-700">Email Notifications</span>
                  <input type="checkbox" class="w-5 h-5" />
                </div>

                <div class="flex items-center justify-between">
                  <span class="font-bold text-slate-700">SMS Notifications</span>
                  <input type="checkbox" class="w-5 h-5" />
                </div>

                <div class="flex items-center justify-between">
                  <span class="font-bold text-slate-700">Interview Reminders</span>
                  <input type="checkbox" class="w-5 h-5" />
                </div>

              </div>

            </div>
            <div v-if="activeTab === 'candidate'" class="space-y-10">

              <header>
                <h1 class="text-3xl font-black text-slate-900 tracking-tight">
                  Candidate Notifications
                </h1>
                <p class="text-slate-500 mt-1 font-medium">
                  Manage notifications related to candidate activity
                </p>
              </header>

              <div class="bg-white border border-slate-100 rounded-3xl p-8 space-y-8">

               
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">Profile Updated</h3>
                    <p class="text-sm text-slate-400">
                      Get notified when a candidate updates their profile.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

              
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">CV Uploaded</h3>
                    <p class="text-sm text-slate-400">
                      Receive alerts when a candidate uploads a new CV.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

              
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">Candidate Shortlisted</h3>
                    <p class="text-sm text-slate-400">
                      Be notified when a candidate is shortlisted.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

                
                <div class="flex items-center justify-between">
                  <div>
                    <h3 class="font-bold text-slate-800">Candidate Rejected</h3>
                    <p class="text-sm text-slate-400">
                      Get notified when a candidate is rejected.
                    </p>
                  </div>
                  <input type="checkbox" class="w-5 h-5 accent-indigo-600" />
                </div>

              </div>

            </div>



        </div>
      </main>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const activeTab = ref('profile')

const activeClass =
  "bg-indigo-50 text-indigo-600 p-3 rounded-xl cursor-pointer flex items-center gap-3"

const inactiveClass =
  "text-slate-400 hover:text-indigo-600 p-3 rounded-xl cursor-pointer flex items-center gap-3 transition-colors"
</script>

<style scoped>
.input-style {
  @apply w-full bg-slate-50 border border-slate-100 rounded-2xl px-5 py-4
  focus:bg-white focus:ring-4 focus:ring-indigo-600/10
  focus:border-indigo-600 outline-none transition-all font-bold;
}

.label {
  @apply text-[10px] font-black text-slate-400 uppercase tracking-widest;
}
</style>
