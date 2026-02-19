<template>
  <span ref="target">{{ displayValue }}</span>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  end: { type: Number, required: true },
  duration: { type: Number, default: 2000 },
  delay: { type: Number, default: 500 } // Default delay of 500ms (0.5s)
})

const displayValue = ref(0)
const target = ref(null)
const hasAnimated = ref(false)

const startAnimation = () => {
  if (hasAnimated.value) return
  hasAnimated.value = true

  // Apply the delay before starting the math
  setTimeout(() => {
    let startTimestamp = null
    const step = (timestamp) => {
      if (!startTimestamp) startTimestamp = timestamp
      const progress = Math.min((timestamp - startTimestamp) / props.duration, 1)
      
      // Smooth ease-out curve
      const easeOut = 1 - Math.pow(1 - progress, 3)
      displayValue.value = Math.floor(easeOut * props.end)
      
      if (progress < 1) {
        window.requestAnimationFrame(step)
      }
    }
    window.requestAnimationFrame(step)
  }, props.delay)
}

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      startAnimation()
      observer.disconnect()
    }
  }, {
    threshold: 0.5 
  })

  if (target.value) {
    observer.observe(target.value)
  }
})
</script>