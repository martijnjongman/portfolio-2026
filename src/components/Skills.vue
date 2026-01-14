<script setup>
// Imports
import { onMounted } from 'vue'
import gsap from 'gsap'

// Data json objects
const skillCategories = [
  {
    title: 'UX & UI Design',
    skills: [
      'Design systems',
      'Accessibility',
      'UX Research',
      'Content Design',
      'User Testing',
      'Adobe Suite',
      'Figma',
    ],
  },
  {
    title: 'Front-end Development',
    skills: [
      'HTML',
      'CSS & SCSS',
      'Javascript',
      'VueJS',
      'Tailwind',
      'GSAP',
      'Wordpress & Umbraco',
    ],
  },
]

onMounted(() => {
  // Only animate skill items after 1024px viewport width
  gsap.matchMedia().add('(min-width: 1024px)', () => {
    gsap.from('.skill-item', {
      scrollTrigger: {
        trigger: '.skill-item',
        start: 'top 85%',
        toggleActions: 'reverse play reverse play',
      },
      x: 30,
      opacity: 0,
      stagger: 0.1,
      duration: 0.3,
      ease: 'power4.out',
    })
  })
})
</script>

<template>
  <section id="skills" class="overflow-x-hidden px-4 pb-10">
    <div class="w-full mx-auto lg:w-4xl">
      <h2 class="h2-title lg:mb-8 xl:-ml-40">Skills & Knowledge</h2>

      <div class="flex flex-col gap-8 lg:flex-row lg:gap-0">
        <div v-for="category in skillCategories" class="w-full flex flex-col lg:w-1/2">
          <h3 class="text-sm mb-2 lg:text-xl">{{ category.title }}</h3>
          <ul>
            <li
              class="skill-item border-black/25 border-t py-2 text-xl last:border-b lg:py-4 lg:text-3xl"
              v-for="skill in category.skills"
              :key="skill"
            >
              {{ skill }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>
