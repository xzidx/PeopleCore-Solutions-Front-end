<template>
  <!-- NAVBAR -->
  <header class="max-w-7xl mx-auto px-6 py-6 flex justify-between items-center">
    <h1 class="text-2xl font-bold">PeopleCore</h1>

    <nav class="hidden md:flex gap-8 text-gray-300">
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/">Jobs</NuxtLink>
      <NuxtLink to="/">Services</NuxtLink>
      <NuxtLink to="/">Pages</NuxtLink>
    </nav>

    <button class="border border-yellow-400 px-4 py-2 rounded-full">
      Login
    </button>
  </header>

  <!-- HERO -->
  <section class="text-center py-24 px-6">
    <p class="uppercase text-sm tracking-widest text-gray-400">
      Jobs Portal USA
    </p>

    <h2 class="text-4xl md:text-6xl font-bold mt-6">
      Unlock Your Skill <br />
      Potential With <span class="text-indigo-400">PeopleCore</span>
    </h2>

    <p class="mt-6 text-gray-400 max-w-2xl mx-auto">
      Find jobs, apply online, and attend interviews remotely.
      We help companies and candidates connect easily.
    </p>

    <button class="mt-10 bg-yellow-400 text-black px-8 py-4 rounded-full font-semibold">
      Get Started
    </button>

    <!-- Stats -->
    <div class="mt-16 flex justify-center gap-10">
      <div class="bg-white/10 px-8 py-4 rounded-xl">
        <p class="text-2xl font-bold">850+</p>
        <p class="text-sm text-gray-400">Companies</p>
      </div>
      <div class="bg-white/10 px-8 py-4 rounded-xl">
        <p class="text-2xl font-bold">424+</p>
        <p class="text-sm text-gray-400">Jobs</p>
      </div>
    </div>
  </section>

  <!-- JOB SECTION -->
  <section class="max-w-7xl mx-auto px-6 py-20 grid md:grid-cols-2 gap-12 items-center">
    <img
      src="https://images.unsplash.com/photo-1521737604893-d14cc237f11d"
      class="rounded-2xl"
      alt="Jobs"
    />

    <div>
      <span class="inline-block bg-yellow-400 text-black px-4 py-1 rounded-full mb-4">
        30+ New Jobs
      </span>

      <h3 class="text-4xl font-bold mb-6">
        Find Your <span class="text-indigo-400">Dream Job</span> <br />
        And Career Path
      </h3>

      <ul class="space-y-3 text-gray-400">
        <li>✔ Thousands of jobs available</li>
        <li>✔ Easy apply for the right job</li>
        <li>✔ Remote interview support</li>
      </ul>

      <button class="mt-8 border border-yellow-400 px-6 py-3 rounded-full">
        Browse All Jobs
      </button>
    </div>
  </section>

  <!-- TESTIMONIALS -->
  <section class="max-w-7xl mx-auto px-6 py-20">
    <h3 class="text-center text-3xl font-bold mb-12">
      Bringing Out The Potential In You
    </h3>

    <div class="grid md:grid-cols-2 gap-8">
      <div class="bg-white/10 p-6 rounded-xl">
        <p class="text-yellow-400">★★★★★</p>
        <p class="mt-4 text-gray-300">
          “Hiring is faster and easier now.”
        </p>
        <p class="mt-4 text-sm text-gray-400">HR Manager</p>
      </div>

      <div class="bg-white/10 p-6 rounded-xl">
        <p class="text-yellow-400">★★★★★</p>
        <p class="mt-4 text-gray-300">
          “Modern and easy-to-use platform.”
        </p>
        <p class="mt-4 text-sm text-gray-400">Employer</p>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="text-center py-10 text-gray-400">
    © 2026 PeopleCore Solutions (USA)
  </footer>
</template>
