<template>
  <section class="max-w-5xl mx-auto px-6 py-16 text-sm">
    <div class="mb-10">
      <span class="bg-blue-600 text-white px-4 py-2 rounded-full text-xs">
        HR Dashboard
      </span>
      <h1 class="text-4xl font-bold mt-4">
        Post a New Job
      </h1>
      <p class="text-gray-600 mt-2">
        Create a structured job post for candidates.
      </p>
    </div>

    <form
      @submit.prevent="submitJob"
      class="bg-white rounded-2xl shadow border p-8 space-y-10"
    >
      <section>
        <h2 class="text-xl font-semibold mb-4">Basic Information</h2>

        <div class="grid md:grid-cols-2 gap-6">
          <div>
            <label>Job Title</label>
            <input v-model="form.title" class="input" />
          </div>

          <div>
            <label>Category</label>
            <select v-model="form.category" class="input">
              <option value="">Select</option>
              <option>IT & Software</option>
              <option>Design</option>
              <option>Marketing</option>
            </select>
          </div>

          <div>
            <label>Job Type</label>
            <select v-model="form.type" class="input">
              <option>Full Time</option>
              <option>Part Time</option>
              <option>Contract</option>
              <option>Remote</option>
            </select>
          </div>

          <div>
            <label>Location</label>
            <input v-model="form.location" class="input" />
          </div>

          <div>
            <label>Salary</label>
            <input v-model="form.salary" class="input" />
          </div>

          <div>
            <label>Deadline</label>
            <input type="date" v-model="form.deadline" class="input" />
          </div>
        </div>
      </section>

      <section>
        <h2 class="text-xl font-semibold mb-4">Responsibilities</h2>
        <textarea
          v-model="form.responsibilities"
          rows="5"
          class="textarea"
          placeholder="- Develop web applications..."
        ></textarea>
      </section>

      <section>
        <h2 class="text-xl font-semibold mb-4">Requirements</h2>
        <textarea
          v-model="form.requirements"
          rows="5"
          class="textarea"
          placeholder="- Strong knowledge of JavaScript..."
        ></textarea>
      </section>

      <section>
        <h2 class="text-xl font-semibold mb-4">Benefits</h2>
        <textarea
          v-model="form.benefits"
          rows="4"
          class="textarea"
          placeholder="- Competitive salary..."
        ></textarea>
      </section>

      <div class="flex justify-end gap-4">
        <button type="reset" class="btn-secondary">
          Clear
        </button>

        <button type="submit" class="btn-primary">
          Publish Job
        </button>
      </div>
    </form>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  title: '',
  category: '',
  type: '',
  location: '',
  salary: '',
  deadline: '',
  responsibilities: '',
  requirements: '',
  benefits: '',
})

const submitJob = async () => {
  await $fetch('/api/company/jobs', {
    method: 'POST',
    body: form.value,
  })
  alert('Job published')
}
</script>

<style scoped>
.input {
  @apply w-full border rounded-lg px-3 py-2 mt-1;
}
.textarea {
  @apply w-full border rounded-lg px-3 py-2;
}
.btn-primary {
  @apply bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-800;
}
.btn-secondary {
  @apply border px-6 py-3 rounded-lg text-gray-600;
}
</style>
