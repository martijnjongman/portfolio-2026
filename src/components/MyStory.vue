<script setup>
import { onMounted } from 'vue'
import gsap from 'gsap'

onMounted(() => {
  // Only animate story items after 1024px viewport width
  gsap.matchMedia().add('(min-width: 1024px)', () => {
    gsap.from('.gsap-story', {
      scrollTrigger: {
        trigger: '.gsap-story',
        start: 'top 100%',
        toggleActions: 'reverse play reverse play',
      },
      y: -100,
      opacity: 0,
      stagger: 0.2,
    })
  })
})
</script>

<template>
  <section
    id="story"
    class="container mx-auto px-4 flex flex-col lg:flex-row lg:justify-between lg:px-0"
  >
    <div class="w-full lg:w-4xl mx-auto">
      <h2 class="gsap-story h2-title lg:mb-8 xl:-ml-40">My Story</h2>

      <div class="flex flex-col lg:flex-row gap-4 lg:gap-8">
        <p class="gsap-story text-lg lg:text-xl">
          A creative designer with over three years of experience in design and development. My
          focus point is not just on creating beautiful & functional brands and digital
          applications, but on extracting the essence of the brand to create a solution that truly
          represents the company's soul.
        </p>
        <p class="gsap-story lg:mt-1">
          ‍My workflow begins with a good understanding all the requirements and wishes before
          moving on to the next steps. Once everything is clear, I create wireframes to see if the
          concept resonates with the client. The next step involves building a prototype in Figma
          and testing it with end-users. After incorporating the feedback, the prototype moves into
          development with the help of HTML, CSS, JS, Wordpress & Webflow.
          <br />
          <br />
          Outside of work, I’m passionate about sports like volleyball, padel, and tennis. I love
          challenging myself to become the best version of myself in each sport. To stimulate my
          creative mind, I started playing the piano.
        </p>
      </div>
    </div>
  </section>
</template>
