<script lang="ts">
  import { onMount } from "svelte";

  let elemCarousel: HTMLDivElement;
  export let imageIds: string[] = [];
  let timeoutId: ReturnType<typeof setTimeout>;

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

  function autoAdvanceCarousel() {
    const randomTimeout = Math.random() * 1000 + 3000;
    timeoutId = setTimeout(() => {
      carouselRight();
      autoAdvanceCarousel();
    }, randomTimeout);
  }

  function pauseAutoAdvance() {
    if (timeoutId) clearTimeout(timeoutId); // Stop the auto-advance on hover
  }

  function resumeAutoAdvance() {
    autoAdvanceCarousel(); // Restart auto-advance on mouse leave
  }

  onMount(() => {
    autoAdvanceCarousel(); // Start the auto-advance
    return () => clearTimeout(timeoutId); // Use the timeout ID to clear the timeout
  });

</script>

<!-- CAROUSEL -->
 <div
  class='flex  items-center'
  role="group" 
  aria-label="Image carousel" 
  on:mouseenter={pauseAutoAdvance}  
  on:mouseleave={resumeAutoAdvance} 
 >
  <!-- Button: Left -->
  <button 
    type="button" 
    class="btn-icon variant-filled opacity-50  absolute left-1 z-10" 
    on:click={carouselLeft}
  >
    <i class="fa-solid fa-chevron-left" />
  </button>
  <!-- Full Images -->
  <div
    bind:this={elemCarousel}
    class="snap-x snap-mandatory scroll-smooth flex overflow-x-hidden"
  >
    {#each imageIds as imageId}
      <img
        class="snap-center h-[130px] md:h-[260px] rounded-container-token object-contain"
        src={imageId}
        alt={imageId}
        loading="lazy"
      />
    {/each}
  </div>
  <!-- Button: Right -->
  <button
    type="button"
    class="btn-icon variant-filled opacity-50  absolute right-1 z-10 "
    on:click={carouselRight}
  >
    <i class="fa-solid fa-chevron-right" />
  </button>
</div>