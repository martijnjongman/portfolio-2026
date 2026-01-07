<script setup>
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

      // Parallax effect title text
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
      class="relative flex flex-col px-4 mt-14 h-full w-full lg:flex-row lg:w-fit lg:items-center lg:px-[20vw]"
    >
      <div class="group flex flex-col mb-6 lg:absolute lg:left-2 lg:top-40">
        <figure class="w-[25vh] shrink-0 mb-2 overflow-hidden relative">
          <img
            src="../assets/images/portret.png"
            class="w-full aspect-square object-cover lg:grayscale-100 group-hover:grayscale-0 transition"
          />
        </figure>
        <h2 class="text-xl lg:text-3xl font-serif font-medium">Martijn Jongman</h2>
        <p class="text-xs lg:text-sm uppercase">Webdesigner & Developer</p>
      </div>

      <span class="gsap-parallax-text relative leading-none font-serif mb-6 lg:whitespace-nowrap"
        >Projects Gallery</span
      >

      <a
        href="https://beleefbedum.nl/"
        target="_blank"
        class="group gsap-parallax-showcase flex flex-col lg:flex-row mb-6 lg:absolute lg:left-1/5 lg:bottom-0 hover:cursor-pointer"
      >
        <figure
          class="w-full lg:w-[45vh] mb-2 shrink-0 overflow-hidden relative hover:grayscale-0 transition"
        >
          <img
            src="../assets/images/beleef.png"
            class="w-full aspect-video object-contain lg:grayscale-100 group-hover:grayscale-0 transition"
          />
        </figure>
        <div class="flex flex-col lg:ml-4">
          <h2
            class="text-xl lg:text-3xl font-serif font-medium underline lg:no-underline group-hover:underline"
          >
            Beleef Bedum
          </h2>
          <p class="text-xs lg:text-sm uppercase whitespace-nowrap">Webdevelopment</p>
        </div>
      </a>

      <a
        href="https://www.bureaudewit.nl/"
        target="_blank"
        class="group gsap-parallax-showcase flex flex-col mb-6 lg:flex-row lg:absolute lg:left-1/2 lg:top-20"
      >
        <figure
          class="w-full lg:w-[45vh] mb-2 shrink-0 overflow-hidden relative hover:grayscale-0 transition"
        >
          <img
            src="../assets/images/bureau.png"
            class="w-full aspect-video object-contain lg:grayscale-100 group-hover:grayscale-0 transition"
          />
        </figure>
        <div class="flex flex-col lg:ml-4">
          <h2
            class="text-xl lg:text-3xl font-serif font-medium underline lg:no-underline group-hover:underline"
          >
            Bureau de Wit
          </h2>
          <p class="text-xs lg:text-sm uppercase whitespace-nowrap">Webdesign & development</p>
        </div>
      </a>

      <a
        href="https://www.dbkeukens.nl/"
        target="_blank"
        class="group gsap-parallax-showcase flex flex-col lg:flex-row lg:absolute lg:left-3/4 lg:bottom-10"
      >
        <figure
          class="w-full lg:w-[45vh] mb-2 shrink-0 overflow-hidden lg:order-2 relative hover:grayscale-0 transition"
        >
          <img
            src="../assets/images/keukens.png"
            class="w-full aspect-video object-contain lg:grayscale-100 group-hover:grayscale-0 transition"
          />
        </figure>
        <div class="flex flex-col lg:items-end lg:order-1 lg:mr-4">
          <h2
            class="text-xl lg:text-3xl font-serif font-medium underline lg:no-underline group-hover:underline"
          >
            DB Keukens
          </h2>
          <p class="text-xs lg:text-sm uppercase whitespace-nowrap">Webdevelopment</p>
        </div>
      </a>
    </div>
  </section>
</template>
