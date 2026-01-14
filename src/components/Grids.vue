<template>
  <section class="container mx-auto flex flex-col lg:flex-row lg:justify-between gap-10">
    <div>
      <div class="gsap-grid from-left flex flex-col mb-6">
        <figure class="w-2/3 lg:w-[35vw] max-w-2xl mb-2">
          <img clas="w-full h-full object-contain" src="../assets/grids/Fibonacci.svg" />
        </figure>
        <div class="flex flex-col">
          <h3>Fibonacci</h3>
          <p class="tag">Design sequence</p>
        </div>
      </div>
    </div>

    <div class="grid place-items-end mr-4 lg:mt-50">
      <div class="gsap-grid from-right flex flex-col mb-6">
        <figure class="w-full lg:w-[40vw] max-w-3xl aspect-video mb-2">
          <img clas="w-full h-full object-contain" src="../assets/grids/GoldenCanonGrid.svg" />
        </figure>
        <div class="flex flex-col">
          <h3>Golden Canon Grid</h3>
          <p class="tag">Design Grid System</p>
        </div>
      </div>
    </div>
  </section>
</template>
