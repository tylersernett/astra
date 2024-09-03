<script lang="ts">
  import { onMount } from "svelte";
  import Carousel from "./Carousel.svelte";

  let elemCarousel: HTMLDivElement;
  // let imageIds1 = [
  //   "images/emergency.jpg",
  //   "images/ambulance.jpg",
  //   "images/car-collision.jpg",
  //   "images/stretcher.jpg",
  //   "images/dallas-ambulance.jpg",
  //   "images/eblanket.jpg",
  // ];

  let imageIds2 = [
    "images/xray-office.jpg",
    "images/riley-op.png",
    "images/doctor-chart.jpg",
    "images/mri-point.jpg",
    // "images/riley-machine-blue-3.png",
    "images/riley-machine-blue-4.png",
    // "images/riley-machine-blue.png",
    "images/skull-scan.jpg",
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
    }, 3000000);

    return () => clearInterval(interval);
  });
</script>

<!-- Carousel Container with Background Image -->
<div
  class="relative w-full md:h-[324px] bg-cover bg-center bg-fixed"
  style="background-image: url('/images/bg-mag.jpg');"
>
<!-- BLUR -->
<div id='blurred-bg' class="absolute inset-0" ></div>
  <!-- Fade  -->
  <!-- <div class="absolute inset-0 bg-primary-50 opacity-40"></div> -->
  <!-- Gradient -->
  <div    class="absolute inset-0 opacity-60 bg-gradient-to-br variant-gradient-primary-secondary" ></div>

  <!-- <div
    class=" p-4 grid grid-cols-[auto_1fr_auto] gap-4 items-center relative z-10 bg-transparent"
  >
    <Carousel imageIds={imageIds1} />
  </div> -->
  <div
    class="p-4 md:p-8 grid grid-cols-[auto_1fr_auto] gap-4 items-center relative z-10 bg-transparent"
  >
    <Carousel imageIds={imageIds2} />
  </div>
</div>
