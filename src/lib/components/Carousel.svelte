<script lang="ts">
  import { onMount } from "svelte";

  let elemCarousel: HTMLDivElement;
  const unsplashIds = [
    "images/emergency.jpg",
    "images/ambulance.jpg",
    "images/car-collision.jpg",
    "images/dallas-ambulance.jpg",
    "images/eblanket.jpg",
  ];

  function carouselLeft(): void {
    const x =
      elemCarousel.scrollLeft === 0
        ? elemCarousel.clientWidth * elemCarousel.childElementCount // loop
        : elemCarousel.scrollLeft - elemCarousel.clientWidth; // step left
    elemCarousel.scroll(x, 0);
  }

  function carouselRight(): void {
    const x =
      elemCarousel.scrollLeft ===
      elemCarousel.scrollWidth - elemCarousel.clientWidth
        ? 0 // loop
        : elemCarousel.scrollLeft + elemCarousel.clientWidth; // step right
    elemCarousel.scroll(x, 0);
  }

  onMount(() => {
    // Auto-advance carousel every 3 seconds
    const interval = setInterval(() => {
      if (elemCarousel) {
        carouselRight();
      }
    }, 3000);

    return () => clearInterval(interval);
  });
</script>

<!-- Carousel Container with Background Image -->
<div class="relative w-full h-[560px] bg-cover bg-center bg-fixed" style="background-image: url('/images/bg-mag.jpg');">
   <!-- Fade Overlay -->
   <div class="absolute inset-0 bg-primary-50 opacity-40"></div>
   <div class="absolute inset-0 opacity-60 bg-gradient-to-br variant-gradient-primary-secondary"></div>

  <!-- CAROUSEL -->
  <div class="pt-40 p-4 grid grid-cols-[auto_1fr_auto] gap-4 items-center relative z-10 bg-transparent">
    <!-- Button: Left -->
    <button type="button" class="btn-icon variant-filled opacity-50" on:click={carouselLeft}>
      <i class="fa-solid fa-chevron-left" />
    </button>
    <!-- Full Images -->
    <div
      bind:this={elemCarousel}
      class="snap-x snap-mandatory scroll-smooth flex overflow-x-hidden"
    >
      {#each unsplashIds as unsplashId}
        <img
          class="snap-center h-[260px] rounded-container-token"
          src={unsplashId}
          alt={unsplashId}
          loading="lazy"
        />
      {/each}
    </div>
    <!-- Button: Right -->
    <button
      type="button"
      class="btn-icon variant-filled opacity-50"
      on:click={carouselRight}
    >
      <i class="fa-solid fa-chevron-right" />
    </button>
  </div>
</div>