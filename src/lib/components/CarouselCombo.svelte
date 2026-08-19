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
    "images/xray-office.webp",
    "images/riley-op.webp",
    "images/doctor-chart.webp",
    "images/mri-point.webp",
    // "images/riley-machine-blue-3.png",
    "images/riley-machine-blue-4.webp",
    // "images/riley-machine-blue.png",
    "images/skull-scan.webp",
  ];
</script>

<!-- Carousel Container with Background Image -->
<div
  class="relative w-full md:h-[324px] bg-cover bg-center md:bg-fixed"
  style="background-image: url('/images/bg-mag.webp');"
>
<!-- BLUR -->
<div id='blurred-bg' class="absolute inset-0" ></div>
  <!-- Fade  -->
  <!-- <div class="absolute inset-0 bg-primary-50 opacity-40"></div> -->
  <!-- Gradient -->
  <div    class="absolute inset-0 opacity-60 bg-gradient-to-br variant-gradient-primary-secondary" ></div>

  <div
    class="p-4 md:p-8 grid grid-cols-[auto_1fr_auto] items-center relative z-10 bg-transparent"
  >
    <Carousel imageIds={imageIds2} />
  </div>
</div>
