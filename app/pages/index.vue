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
  <div class="bg-white py-16 px-6 md:py-24">
  <div class="max-w-7xl mx-auto">
    
    <div class="text-center mb-16">
      <div class="flex items-center justify-center gap-2 mb-4">
        <i class="fa-solid fa-brain"></i>
        <span class="text-lg font-medium text-gray-900">How It Works</span>
      </div>
      <h2 class="text-5xl md:text-5xl lg:text-5xl font-bold text-blue-500 tracking-tight leading-tight">
        A simple process to help <br class="hidden md:block" /> you hire faster
      </h2>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-x-12 gap-y-16">
      
      <div class="flex flex-col space-y-4">
        <span class="text-4xl font-light text-blue-500">01</span>
        <h3 class="text-xl font-bold text-gray-900">Share Your Hiring Needs</h3>
        <p class="text-gray-500 leading-relaxed text-sm md:text-base">
          Tell us the role you want to fill add skills, experience, and job details we review everything plan hiring path.
        </p>
      </div>

      <div class="flex flex-col space-y-4">
        <span class="text-4xl font-light text-blue-500">02</span>
        <h3 class="text-xl font-bold text-gray-900">Shortlist The Candidates</h3>
        <p class="text-gray-500 leading-relaxed text-sm md:text-base">
          We search, filter, and screen candidates only qualified profiles are selected you get a clean and clear shortlist
        </p>
      </div>

      <div class="flex flex-col space-y-4">
        <span class="text-4xl font-light text-blue-500">03</span>
        <h3 class="text-xl font-bold text-gray-900">Interview & Select</h3>
        <p class="text-gray-500 leading-relaxed text-sm md:text-base">
          We schedule interviews you meet the candidates pick the best match for your team
        </p>
      </div>

      <div class="flex flex-col space-y-4">
        <span class="text-4xl font-light text-blue-500">04</span>
        <h3 class="text-xl font-bold text-gray-900">Final Hiring & Onboarding</h3>
        <p class="text-gray-500 leading-relaxed text-sm md:text-base">
          We guide you through the hiring steps smooth onboarding support start growing with your new team member
        </p>
      </div>

    </div>
  </div>
</div>


<div class="bg-white py-16 px-6 md:py-24">
  <div class="max-w-7xl mx-auto">
    
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-start mb-24">
      
      <div class="space-y-8">
        <div>
          <div class="flex items-center gap-2 mb-4">
            <i class="fa-regular fa-lightbulb"></i>
            <span class="text-lg font-semibold uppercase tracking-wide text-gray-900">Why Choose Us</span>
          </div>
          <h2 class="text-4xl md:text-5xl font-bold text-blue-500 leading-tight max-w-md">
            Hiring made easy, clear, and effective
          </h2>
        </div>
        
        <div class="rounded-2xl overflow-hidden shadow-lg">
          <img src="https://images.unsplash.com/photo-1516321318423-f06f85e504b3?q=80&w=1000&auto=format&fit=crop" alt="Person working" class="w-full h-[400px] object-cover" />
        </div>
      </div>

      <div class="space-y-8 lg:pt-20">
        <div class="grid grid-cols-2 gap-4">
          <div class="rounded-2xl overflow-hidden shadow-md">
            <img src="https://images.unsplash.com/photo-1499750310107-5fef28a66643?q=80&w=500&auto=format&fit=crop" alt="Working" class="w-full h-48 object-cover" />
          </div>
          <div class="rounded-2xl overflow-hidden shadow-md">
            <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?q=80&w=500&auto=format&fit=crop" alt="Meeting" class="w-full h-48 object-cover" />
          </div>
        </div>
        
        <p class="text-gray-600 leading-relaxed max-w-lg">
          We use clean steps and modern tools to speed up your hiring. Only the best and most relevant profiles reach your shortlist. Tech, marketing, finance, sales, admin, healthcare, and more. Clear updates at every step.
        </p>

        <button class="bg-gray-500 text-white px-8 py-3 rounded-xl font-semibold hover:bg-blue-500 transition-colors">
          More About Us 
        </button>
      </div>
    </div>

    <div class="grid grid-cols-2 lg:grid-cols-4 gap-8 pt-12 border-t border-gray-100">
      <div class="space-y-2">
        <div class="text-5xl font-bold text-gray-900">24/7</div>
        <p class="text-sm text-gray-500">Always ready to assist employers and candidates.</p>
      </div>

      <div class="space-y-2">
        <div class="text-5xl font-bold text-gray-900">
          <AnimatedNumber :end="3" />M+
        </div>
        <p class="text-sm text-gray-500">Tech Professionals Trust on Hirehub</p>
      </div>

      <div class="space-y-2">
        <div class="text-5xl font-bold text-gray-900">
          <AnimatedNumber :end="500" />+
        </div>
        <p class="text-sm text-gray-500">Successful Hires Completed Till Now</p>
      </div>

      <div class="space-y-2">
        <div class="text-5xl font-bold text-gray-900">
          <AnimatedNumber :end="98" />%
        </div>
        <p class="text-sm text-gray-500">Client Satisfaction Rate That Speaks for Itself</p>
      </div>
    </div>

  </div>
</div>





 </template>