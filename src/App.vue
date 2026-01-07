<script setup>
import { onMounted, ref } from 'vue'
//Import Components
import Navigation from './components/Navigation.vue'
import HeroGallery from './components/HeroGallery.vue'
import Skills from './components/Skills.vue'
import Grids from './components/Grids.vue'
import MyStory from './components/MyStory.vue'
import FooterComponent from './components/Footer.vue'

// Import GSAP and globally import scroll trigger plugin
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

// Set reactive variable
const mainContent = ref(null)

// Subtle fade in effect
onMounted(() => {
  gsap.from(mainContent.value, {
    opacity: 0,
    duration: 0.6,
    ease: 'power2.out',
  })
})
</script>

<template>
  <Navigation />

  <main ref="mainContent">
    <HeroGallery />
    <Skills />
    <Grids />
    <MyStory />
  </main>

  <FooterComponent />
</template>
