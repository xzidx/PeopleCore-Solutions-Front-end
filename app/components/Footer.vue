<template>
  <section class="bg-white font-sans text-[#1a1a1a] py-20 px-6">
    <div class="max-w-6xl mx-auto">
      
      <div class="text-center mb-24">
        <h2 class="text-4xl md:text-5xl font-serif text-gray-500 mb-2">
          Connecting Talent with Opportunity
        </h2>
        <p class="text-4xl md:text-5xl font-serif mb-8">
          Your career journey starts here.
        </p>
        <NuxtLink 
          to="/contact" 
          class="inline-flex items-center gap-3 bg-black text-white px-8 py-4 rounded-full hover:bg-gray-800 transition-all group"
        >
          Lets Work Together
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="group-hover:translate-x-1 transition-transform"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
        </NuxtLink>
      </div>

      <div class="flex flex-col md:flex-row justify-between items-start gap-12 mb-16 relative">
        
        <div class="max-w-sm">
           <div class="  w-[200px] h-[80px] ">
                <img src="/home/chan-samnang/Documents/Project/PeopleCore-Solutions/PeopleCore-Solutions-Front-end/public/images/logo.png" alt="">
            </div>
          <p class="text-sm leading-relaxed text-gray-600 mb-8">
            Discover thousands of job opportunities and connect with top employers. Our platform helps you apply faster and get hired smarter.
          </p>
          
          <div class="flex gap-5 items-center">
            <NuxtLink to="#" class="hover:opacity-70 transition"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg></NuxtLink>
            <NuxtLink to="#" class="hover:opacity-70 transition"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M8.5 8.5c.7.7 1.3 1.2 2 1.5 1.1.4 2.4.5 3.5.1s2.2-1.2 2.7-2.2"/><path d="M5 12s3.5 1.5 7 1.5 7-1.5 7-1.5"/><path d="M12 2s-4 5.5-4 10 4 10 4 10 4-5.5 4-10-4-10-4-10"/></svg></NuxtLink>
            <NuxtLink to="#" class="hover:opacity-70 transition"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/></svg></NuxtLink>
            <NuxtLink to="#" class="hover:opacity-70 transition"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg></NuxtLink>
            <NuxtLink to="#" class="hover:opacity-70 transition">
              <span class="text-xl font-bold">X</span>
            </NuxtLink>
          </div>
        </div>

        <div class="flex flex-col items-end gap-12 w-full md:w-auto">
         

          <div class="flex flex-col items-end gap-4">
            <nav class="flex gap-4 text-sm font-medium">
              <NuxtLink to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500 text-xl">Home</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span></NuxtLink>
              <NuxtLink to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500 text-xl">Jobs</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span></NuxtLink>
              <NuxtLink to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500 text-xl">Companies</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span></NuxtLink>
              <NuxtLink to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500 text-xl">About</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span></NuxtLink>
              <NuxtLink to="/jobs" 
                class="relative group transition duration-300">
                <span class="group-hover:text-blue-500 text-xl">Contact</span>
                <span class="absolute left-0 -bottom-1 h-[2px] w-0 bg-blue-500 transition-all duration-300 group-hover:w-full"></span></NuxtLink>
            </nav>
            <nav class="flex gap-4 text-[11px] text-gray-500 font-medium">
              <NuxtLink to="/privacy" class="hover:underline">Privacy Policy</NuxtLink>
              <NuxtLink to="/terms" class="hover:underline">Terms Of Services</NuxtLink>
              <NuxtLink to="/cookies" class="hover:underline">Cookie Settings</NuxtLink>
            </nav>
          </div>
        </div>
      </div>

      <hr class="border-gray-300 mb-8" />
      
      <div class="text-center text-[12px] text-gray-500 font-medium">
        @2025 . All Right Reserved nurhasan4421
      </div>

    </div>
  </section>
</template>