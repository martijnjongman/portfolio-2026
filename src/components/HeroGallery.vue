<script setup>
// Imports
import { onMounted, ref, nextTick } from 'vue'
import gsap from 'gsap'

// Set variables
const sectionRef = ref(null)
const containerRef = ref(null)

onMounted(async () => {
  // Wait for the DOM
  await nextTick()

  // Only animate after 1024px viewport width
  gsap.matchMedia().add('(min-width: 1024px)', () => {
    gsap.context(() => {
      // Set total width of container
      const totalWidth = containerRef.value.scrollWidth

      // Calculate scroll amount
      const amountToScroll = totalWidth - window.innerWidth

      // Set scroll animation
      const scrollAnimation = gsap.to(containerRef.value, {
        x: -amountToScroll,
        ease: 'none',
        scrollTrigger: {
          trigger: sectionRef.value,
          pin: true,
          scrub: 1,
          end: `+=${amountToScroll}`,
          invalidateOnRefresh: true,
        },
      })

      // Get images for parallax effect
      const images = gsap.utils.toArray('.gsap-parallax-showcase')

      // Loop through images and add parallax effect
      images.forEach((img) => {
        gsap.fromTo(
          img,
          { x: -400 },
          {
            x: 400,
            ease: 'none',
            scrollTrigger: {
              trigger: img.parentElement,
              containerAnimation: scrollAnimation,
              horizontal: true,
              start: 'left right',
              end: 'right left',
              scrub: true,
            },
          },
        )
      })

      // Parallax effect project__title text
      gsap.to('.gsap-parallax-text', {
        x: -200,
        ease: 'none',
        scrollTrigger: {
          trigger: '.gsap-parallax-text',
          containerAnimation: scrollAnimation,
          horizontal: true,
          start: 'left right',
          end: 'right left',
          scrub: true,
        },
      })
    }, sectionRef.value)
  })
})
</script>

<template>
  <h1 class="sr-only">Portfolio Website Martijn Jongman</h1>

  <section id="hero-gallery" ref="sectionRef" class="relative w-full overflow-hidden lg:h-screen">
    <div
      ref="containerRef"
      class="relative flex flex-col px-4 mt-16 h-full w-full lg:flex-row lg:w-fit lg:items-center lg:px-96"
    >
      <div class="group flex flex-col mb-6 lg:absolute lg:left-2 lg:top-40">
        <figure class="relative w-[50vw] max-w-3xs shrink-0 mb-2 overflow-hidden">
          <img
            src="../assets/images/portret.png"
            class="w-full aspect-square object-cover lg:grayscale-100 group-hover:grayscale-0 transition"
          />
        </figure>
        <h3>Martijn Jongman</h3>
        <p class="tag">Webdesigner & Developer</p>
      </div>

      <span class="gsap-parallax-text relative leading-none font-serif mb-6 lg:whitespace-nowrap"
        >Projects Gallery</span
      >

      <a
        href="https://beleefbedum.nl/"
        target="_blank"
        class="group gsap-parallax-showcase flex flex-col mb-6 lg:flex-row lg:absolute lg:left-1/5 lg:bottom-0"
      >
        <figure class="project__figure">
          <img class="project__image" src="../assets/images/beleef.png" />
        </figure>
        <div class="flex flex-col lg:ml-4">
          <h3 class="project__title">Beleef Bedum</h3>
          <p class="tag">Webdevelopment</p>
        </div>
      </a>

      <a
        href="https://www.bureaudewit.nl/"
        target="_blank"
        class="group gsap-parallax-showcase flex flex-col mb-6 lg:flex-row lg:absolute lg:left-1/2 lg:top-20"
      >
        <figure class="project__figure">
          <img class="project__image" src="../assets/images/bureau.png" />
        </figure>
        <div class="flex flex-col lg:ml-4">
          <h3 class="project__title">Bureau de Wit</h3>
          <p class="tag">Webdesign & development</p>
        </div>
      </a>

      <a
        href="https://www.dbkeukens.nl/"
        target="_blank"
        class="group gsap-parallax-showcase flex flex-col lg:flex-row lg:absolute lg:left-3/4 lg:bottom-10"
      >
        <figure class="project__figure lg:order-2">
          <img class="project__image" src="../assets/images/keukens.png" />
        </figure>
        <div class="flex flex-col lg:items-end lg:order-1 lg:mr-4">
          <h3 class="project__title">DB Keukens</h3>
          <p class="tag">Webdevelopment</p>
        </div>
      </a>
    </div>
  </section>
</template>

<style>
@reference "tailwindcss";
.project__figure {
  @apply w-full mb-2 shrink-0 overflow-hidden relative transition hover:grayscale-0 lg:w-[45vh] lg:grayscale-100;
}
.project__img {
  @apply w-full aspect-video object-contain;
}
.project__title {
  @apply underline group-hover:underline lg:no-underline;
}
</style>
