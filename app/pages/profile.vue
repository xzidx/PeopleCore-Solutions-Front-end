<template>
  <div class="min-h-screen w-[100%] bg-[#F8F9FB] flex items-center justify-center p-4 md:p-8 font-sans text-slate-900 mt-[150px]">
    
    <div class="w-full max-w-8xl bg-white rounded-[2rem] flex overflow-hidden min-h-[800px] border border-slate-100">
      
      <aside class="w-64 border-r border-slate-50 bg-[#FBFBFC] p-8 hidden lg:flex flex-col shrink-0">
        <div class="flex items-center gap-2 text-slate-400 mb-10 hover:text-indigo-600 cursor-pointer transition-all group">
          <i class="fa-solid fa-chevron-left text-[10px] group-hover:-translate-x-1 transition-transform"></i>
          <span class="text-xs font-bold uppercase tracking-widest">Settings</span>
        </div>

        <nav class="space-y-10">
          <div>
            <h3 class="text-[10px] font-black text-slate-300 uppercase tracking-[0.2em] mb-4">Organization</h3>
            <ul class="space-y-4 text-sm font-bold text-slate-500">
              <li class="hover:text-indigo-600 cursor-pointer transition-colors">General</li>
              <li class="hover:text-indigo-600 cursor-pointer transition-colors">Recruitment Flow</li>
              <li class="hover:text-indigo-600 cursor-pointer transition-colors">Team Access</li>
            </ul>
          </div>

          <div>
            <h3 class="text-[10px] font-black text-slate-300 uppercase tracking-[0.2em] mb-4">My Account</h3>
            <ul class="space-y-2 text-sm font-bold">
              <li class="bg-indigo-50 text-indigo-600 p-3 rounded-xl cursor-pointer flex items-center gap-3">
                <i class="fa-regular fa-user"></i> My Profile
              </li>
              <li class="text-slate-400 hover:text-indigo-600 p-3 rounded-xl cursor-pointer flex items-center gap-3 transition-colors">
                <i class="fa-solid fa-shield-halved"></i> Security
              </li>
            </ul>
          </div>
        </nav>
      </aside>

      <main class="flex-1 p-8 md:p-12 lg:p-16 overflow-y-auto">
        <div class="max-w-4xl mx-auto">
          <header class="mb-12">
            <h1 class="text-3xl font-black text-slate-900 tracking-tight">My Profile</h1>
            <p class="text-slate-500 mt-1 font-medium">Manage your personal recruiter settings</p>
          </header>

          <div class="grid grid-cols-1 xl:grid-cols-12 gap-12 items-start">
            
            <div class="xl:col-span-7 space-y-12">
              <section class="space-y-4">
                <h2 class="text-sm font-bold text-slate-900">Your Profile Photo</h2>
                <div class="flex flex-wrap items-center gap-10">
                  <img 
                    src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?q=80&w=200&auto=format&fit=crop" 
                    class="w-24 h-24 rounded-3xl object-cover shadow-lg ring-4 ring-white" 
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
                    <p class="text-[11px] text-slate-400 font-medium tracking-wide">Recommended: 256x256px. PNG or JPG.</p>
                  </div>
                </div>
              </section>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="space-y-2">
                  <label class="text-[10px] font-black text-slate-400 uppercase tracking-widest">First Name</label>
                  <input type="text" value="Julian" class="w-full bg-slate-50 border border-slate-100 rounded-2xl px-5 py-4 focus:bg-white focus:ring-4 focus:ring-indigo-600/10 focus:border-indigo-600 outline-none transition-all font-bold" />
                </div>
                <div class="space-y-2">
                  <label class="text-[10px] font-black text-slate-400 uppercase tracking-widest">Last Name</label>
                  <input type="text" value="Hernandez" class="w-full bg-slate-50 border border-slate-100 rounded-2xl px-5 py-4 focus:bg-white focus:ring-4 focus:ring-indigo-600/10 focus:border-indigo-600 outline-none transition-all font-bold" />
                </div>
                <div class="md:col-span-2 space-y-2">
                  <label class="text-[10px] font-black text-slate-400 uppercase tracking-widest">Email Address</label>
                  <div class="flex gap-3">
                    <input type="email" value="julian.hernandez@recruit.com" disabled class="flex-1 bg-slate-100 border border-slate-200 rounded-2xl px-5 py-4 text-slate-400 font-bold cursor-not-allowed" />
                    <button class="px-6 py-4 bg-white border border-slate-200 rounded-2xl font-bold text-sm hover:bg-slate-50 transition-all">Edit</button>
                  </div>
                </div>
                <div class="md:col-span-2 space-y-2">
                  <label class="text-[10px] font-black text-slate-400 uppercase tracking-widest">Phone Number</label>
                  <input type="tel" value="+1 555 012 3456" class="w-full bg-slate-50 border border-slate-100 rounded-2xl px-5 py-4 focus:bg-white focus:ring-4 focus:ring-indigo-600/10 focus:border-indigo-600 outline-none transition-all font-bold" />
                </div>
              </div>

              <div class="flex items-center gap-4">
                <div class="w-12 h-6 bg-indigo-600 rounded-full relative shadow-inner cursor-pointer">
                  <div class="absolute right-1 top-1 w-4 h-4 bg-white rounded-full shadow-md"></div>
                </div>
                <span class="text-sm font-bold text-slate-700">Display phone number on my profile</span>
              </div>
            </div>

            <div class="xl:col-span-5">
              <div class="bg-indigo-600 rounded-[2.5rem] p-10 text-white shadow-2xl shadow-indigo-200 relative overflow-hidden">
                <div class="relative z-10">
                  <h3 class="text-2xl font-black leading-tight mb-4">Build Candidate Trust!</h3>
                  <p class="text-indigo-100 text-sm font-medium leading-relaxed">
                    Your photo will appear on recruitment emails and interview booking links. This helps candidates associate your agency with a friendly face.
                  </p>
                </div>
                <div class="mt-8 flex justify-end">
                   <i class="fa-solid fa-user-check text-6xl opacity-20"></i>
                </div>
                <div class="absolute -bottom-10 -right-10 w-40 h-40 bg-white opacity-5 rounded-full"></div>
              </div>
            </div>

          </div>
        </div>
      </main>
    </div>
  </div>
</template>