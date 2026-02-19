<template>
  <section class="max-w-4xl mx-auto px-6 py-16 text-lg">
    <div class="mb-10">
      <span class="bg-orange-500 text-white text-sm px-4 py-2 rounded-full">
        Post New Job
      </span>
      <h1 class="text-4xl font-bold mt-4">
        Create a New Job Opportunity
      </h1>
      <p class="text-gray-600 mt-2">
        Fill in the details below to publish a new job opening.
      </p>
    </div>


    <form
      @submit.prevent="submitJob"
      class="bg-white shadow-lg rounded-2xl p-8 space-y-6 border"
    >
      <div>
        <label class="block text-sm font-medium mb-1">Job Title</label>
        <input
          v-model="form.title"
          type="text"
          placeholder="Frontend Developer"
          class="w-full rounded-lg border-gray-300 focus:ring-blue-500"
          required
        />
      </div>

      <div>
        <label class="block text-sm font-medium mb-1">Category</label>
        <select
          v-model="form.category"
          class="w-full rounded-lg p-2 border-gray-300 text-sm focus:ring-blue-500"
          required
        >
          <option value="">Select category</option>
          <option>IT & Software</option>
          <option>Design</option>
          <option>Marketing</option>
          <option>Finance</option>
          <option>Human Resource</option>
        </select>
      </div>

      <div class="grid md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium mb-1">Job Type</label>
          <select
            v-model="form.type"
            class="w-full rounded-lg p-2 border-gray-300 text-sm focus:ring-blue-500"
            required
          >
            <option value="">Select type</option>
            <option>Full Time</option>
            <option>Part Time</option>
            <option>Contract</option>
            <option>Internship</option>
            <option>Remote</option>
          </select>
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Location</label>
          <input
            v-model="form.location"
            type="text"
            placeholder="Phnom Penh / Remote"
            class="w-full rounded-lg border-gray-300 focus:ring-blue-500"
            required
          />
        </div>
      </div>

      <div class="grid md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium mb-1">Salary</label>
          <input
            v-model="form.salary"
            type="text"
            placeholder="$800 – $1,500"
            class="w-full rounded-lg border-gray-300 focus:ring-blue-500"
          />
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Deadline</label>
          <input
            v-model="form.deadline"
            type="date"
            class="w-full rounded-lg border-gray-300 focus:ring-blue-500"
            required
          />
        </div>
      </div>

      <!-- Description -->
      <div>
        <label class="block text-sm font-medium mb-1">
          Job Description
        </label>
        <textarea
          v-model="form.description"
          rows="6"
          class="w-full rounded-lg border-gray-300 focus:ring-blue-500"
          placeholder="Describe job responsibilities, requirements, and benefits..."
          required
        ></textarea>
      </div>

      <div class="flex justify-end gap-4">
        <button
          type="reset"
          class="px-6 py-3 border rounded-lg text-gray-600 hover:bg-gray-100"
        >
          Clear
        </button>

        <button
          type="submit"
          class="px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-800 transition flex items-center gap-2"
        >
          <i class="fa-solid fa-paper-plane"></i>
          Publish Job
        </button>
      </div>
    </form>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  title: 'Full Stack Developer',
  description: '        We are looking for a Full Stack Developer who can work on both frontend and backend development to deliver complete, high-quality web solutions.',
  salary: '650$ – 1,200$',
  location: 'Phnom Penh',
  type: '',
  category: '',
  deadline: '',
})

const submitJob = async () => {
  try {
    console.log('Submitting Job:', form.value)

    // Example API call
    await $fetch('/api/company/jobs', {
      method: 'POST',
      body: form.value,
    })

    alert('Job posted successfully!')
  } catch (error) {
    console.error(error)
    alert('Failed to post job')
  }
}
</script>
