<script setup>
import { ref } from 'vue'

// Reactive variable to toggle menu
let showMenu = ref(false)
</script>

<template>
  <header class="fixed z-30 top-0">
    <div
      class="z-20 relative flex justify-between items-center w-screen bg-off-white lg:px-10 lg:py-8 lg:bg-transparent"
    >
      <a href="/" class="ml-5 uppercase font-sans font-medium text-sm">Martijn Jongman</a>

      <button
        @click="showMenu = !showMenu"
        id="toggle-menu"
        class="size-16 p-6 cursor-pointer hover:bg-gold"
        aria-label="toggle-menu"
      >
        <svg viewBox="0 0 14 14" class="w-full h-full" xmlns="http://www.w3.org/2000/svg">
          <line
            x1="0"
            y1="4"
            x2="14"
            y2="4"
            stroke="black"
            stroke-width="1.5"
            class="transition-all duration-300 origin-center"
            :class="showMenu ? 'rotate-45 translate-y-0.5 -translate-x-0.5' : ''"
          />
          <line
            x1="0"
            y1="10"
            x2="14"
            y2="10"
            stroke="black"
            stroke-width="1.5"
            class="transition-all duration-300 origin-center"
            :class="showMenu ? '-rotate-45 -translate-y-0.5 -translate-x-0.5' : ''"
          />
        </svg>
      </button>
    </div>

    <Transition
      enter-active-class="transition duration-150 ease-out"
      enter-from-class="opacity-0 -translate-y-20"
      enter-to-class="opacity-100"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0 -translate-y-20"
    >
      <nav
        v-if="showMenu"
        aria-label="menu"
        class="z-10 fixed inset-0 w-screen h-screen py-14 bg-off-white lg:py-28"
      >
        <ul
          class="flex flex-col h-full items-center justify-center gap-6 font-serif font-medium text-3xl lg:text-6xl"
        >
          <li class="relative">
            <a @click="showMenu = !showMenu" href="#hero-gallery" class="hover:underline">
              Gallery
              <span class="number">1</span>
            </a>
          </li>
          <li class="relative">
            <a @click="showMenu = !showMenu" href="#skills" class="hover:underline">
              Skills & Knowledge
              <span class="number">2</span>
            </a>
          </li>
          <li class="relative">
            <a @click="showMenu = !showMenu" href="#story" class="hover:underline">
              My Story
              <span class="number">3</span>
            </a>
          </li>
          <li class="relative">
            <a @click="showMenu = !showMenu" href="#footer" class="hover:underline">
              Contact
              <span class="number">4</span>
            </a>
          </li>
        </ul>
      </nav>
    </Transition>
  </header>
</template>

<style>
@reference "tailwindcss";
.number {
  @apply absolute -right-4 -top-4 lg:-right-8;
}
</style>
