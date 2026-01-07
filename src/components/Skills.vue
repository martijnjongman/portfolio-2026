<script setup>
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
    <div class="w-full lg:w-4xl mx-auto">
      <h2 class="h2-title relative font-serif text-4xl lg:text-7xl mb-4 lg:mb-8 w-fit xl:-ml-40">
        Skills & Knowledge
      </h2>

      <div class="flex flex-col lg:flex-row gap-8 lg:gap-0">
        <div v-for="category in skillCategories" class="w-full lg:w-1/2 flex flex-col">
          <h3 class="text-sm lg:text-xl mb-2">{{ category.title }}</h3>
          <ul>
            <li
              class="skill-item border-black/25 border-t py-2 lg:py-4 text-xl lg:text-3xl last:border-b"
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
