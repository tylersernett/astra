<script lang="ts">
  import { onMount } from "svelte";

  let elemCarousel: HTMLDivElement;
  export let imageIds: string[] = [];

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
  let timeoutId: number; // Declare a variable to store the timeout ID

  function autoAdvanceCarousel() {
    if (elemCarousel) {
      carouselRight();
    }

    // Set a random timeout between 3 and 4 seconds (3000 to 4000 ms)
    const randomTimeout = Math.random() * 1000 + 3000;
    timeoutId = setTimeout(autoAdvanceCarousel, randomTimeout) as unknown as number;
  }

  // Start the auto-advance
  autoAdvanceCarousel();

  return () => clearTimeout(timeoutId); // Use the timeout ID to clear the timeout
  });
</script>

<!-- CAROUSEL -->
  <!-- Button: Left -->
  <button type="button" class="btn-icon variant-filled opacity-50" on:click={carouselLeft}>
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
    class="btn-icon variant-filled opacity-50"
    on:click={carouselRight}
  >
    <i class="fa-solid fa-chevron-right" />
  </button>