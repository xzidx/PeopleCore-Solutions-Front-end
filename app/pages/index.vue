<script setup>
// In Nuxt 3, if your file is in components/CardJob.vue, 
// it is auto-imported. No 'import' statement needed!

const jobs = ref([
  {
    id: 1,
    company: "Amazon",
    logoUrl: "https://upload.wikimedia.org/wikipedia/commons/4/4a/Amazon_icon.svg",
    postedAt: "5 days ago",
    jobTitle: "Senior UI/UX Designer",
    tags: ["Part-time", "Senior level"],
    salary: "120",
    location: "San Francisco, CA"
  },
  {
    id: 2,
    company: "Google",
    logoUrl: "https://upload.wikimedia.org/wikipedia/commons/c/c1/Google_Logo.svg",
    postedAt: "2 days ago",
    jobTitle: "Product Designer",
    tags: ["Full-time", "Mid level"],
    salary: "145",
    location: "Mountain View, CA"
  }
])
</script>


<template>
  <div class="bg-white w-[100%] h-screen max-h-screen flex justify-center items-center gap-5 pt-[80px]">
        <div class=" w-[700px] h-[500px] ">
            <img src="/../public/images/jobs-success.jpg" alt="" class=" w-[100%] h-[100%] shadow-2xl border-4 ">
        </div>
        <div class="bg-white w-[800px] h-[700px] flex justify-center items-center ">
              

                <div class="max-w-4xl space-y-10 ">
                  <div class="flex items-center gap-2 text-[#0a1f1a]">
                    <i class="fa-solid fa-award text-black"></i>
                    <span class="text-lg font-semibold tracking-wide text-black ">We Help You Find Skilled Talent</span>
                  </div>

                  <h1 class="text-2xl md:text-7xl font-bold tracking-tight leading-[2.`] text-black">
                    Find the Right Job.<br />
                    <span class=" text-black">Hire the Right Talent.</span>
                  </h1>

                  <p class="max-w-xl text-lg text-gray-600 leading-relaxed text-black">
                    Our HR experts use a clean workflow to attract the right candidates, 
                    screen them, and deliver top talent that fits your company culture.
                  </p>

                    <div class="relative max-w-md group">
                      <input 
                        type="text" 
                        placeholder="Search for talent..." 
                        class="w-full bg-blue-500 text-white placeholder-white rounded-3xl py-5 pl-8 pr-16 text-lg focus:outline-none transition-all"
                      />
                      <button class="absolute right-2 top-2 h-12 w-12 flex items-center justify-center rounded-full bg-white text-blue hover:scale-105 transition-transform">
                          <i class="fa-solid fa-magnifying-glass"></i>                            
                      </button>
                    </div>
                </div>
                
        </div>
  </div>
  

  <div class="w-[100%] h-[200px] text-center">
          <span class="text-black text-3xl font-semibold font-sans ">Our Trusted Supporters</span>
          <div class=" w-[100%] h-[130px] flex justify-center items-center gap-10 mt-[30px]">
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/smart-spp.jpg" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/aclida-bank.jpg" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/wing-spp.png" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/aba-spp.png" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/rolya-spp.jpg" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/air-port.jpg" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                <div class="bg-red-500 w-[170px] h-[100px] bg-white rounded-2xl border-2 border-gray-200"><img src="/../public/images/skillbridge.jpg" alt="" class="w-[100%] h-[100%] rounded-2xl"></div>
                
          </div>
  </div>
  <div class="h-[600px] flex items-center justify-center p-6 gap-5">
    
    <CardJob 
      company="Amazon"
      logo-url="https://upload.wikimedia.org/wikipedia/commons/4/4a/Amazon_icon.svg"
      posted-at="5 days ago"
      job-title="Senior UI/UX Designer"
      :tags="['Part-time', 'Senior']"
      salary="120"
      location="San Francisco, CA"
       info="We are expanding our design department and looking for talented individuals to help us build the next generation of products"
    />

    <CardJob 
      company="Google"
      logo-url="https://upload.wikimedia.org/wikipedia/commons/c/c1/Google_Logo.svg"
      posted-at="1 day ago"
      job-title="Lead Interaction Designer"
      :tags="['Full-time', 'Remote']"
      salary="165"
      location="Mountain View, CA"
      info="We are expanding our design department and looking for talented individuals to help us build the next generation of products"
    />

    <CardJob 
      company="Figma"
      logo-url="https://upload.wikimedia.org/wikipedia/commons/3/33/Figma-logo.svg"
      posted-at="2 hours ago"
      job-title="Product Designer"
      :tags="['Contract', 'Mid-level']"
      salary="95"
      location="New York, NY"
       info="We are expanding our design department and looking for talented individuals to help us build the next generation of products"
    />

    <CardJob 
      company="Figma"
      logo-url="https://upload.wikimedia.org/wikipedia/commons/3/33/Figma-logo.svg"
      posted-at="2 hours ago"
      job-title="Product Designer"
      :tags="['Contract', 'Mid-level']"
      salary="95"
      location="New York, NY"
       info="We are expanding our design department and looking for talented individuals to help us build the next generation of products"
    />
  </div>







 </template>