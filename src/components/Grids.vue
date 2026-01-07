<template>
  <section class="container mx-auto flex flex-col lg:flex-row lg:justify-between gap-10">
    <div>
      <div class="gsap-grid from-left flex flex-col mb-6">
        <figure class="w-2/3 lg:w-[35vw] max-w-2xl mb-2">
          <img clas="w-full aspect-video object-contain" src="../assets/grids/Fibonacci.svg" />
        </figure>
        <div class="flex flex-col">
          <h2 class="text-xl lg:text-3xl font-serif font-medium">Fibonacci</h2>
          <p class="text-xs lg:text-sm uppercase tracking-wide">Design sequence</p>
        </div>
      </div>
    </div>

    <div class="grid place-items-end mr-4 lg:mt-50">
      <div class="gsap-grid from-right flex flex-col mb-6">
        <figure class="w-full lg:w-[40vw] max-w-3xl aspect-video mb-2">
          <img
            clas="w-full aspect-video object-contain"
            src="../assets/grids/GoldenCanonGrid.svg"
          />
        </figure>
        <div class="flex flex-col">
          <h2 class="text-xl lg:text-3xl font-serif font-medium">Golden Canon Grid</h2>
          <p class="text-xs lg:text-sm uppercase tracking-wide">Design Grid System</p>
        </div>
      </div>
    </div>
  </section>
</template>
