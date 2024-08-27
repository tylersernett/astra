<script lang="ts">
  import "../app.css";
  import {
    AppShell,
    AppBar,
    type DrawerSettings,
  } from "@skeletonlabs/skeleton";
  import {
    initializeStores,
    Drawer,
    getDrawerStore,
  } from "@skeletonlabs/skeleton";
  import CarouselCombo from "../lib/components/CarouselCombo.svelte";

  initializeStores();

  const drawerStore = getDrawerStore();
  const drawerSettings: DrawerSettings = {
    // Provide your property overrides:
    position: "right",
    bgDrawer: "bg-surface-50 ",
    bgBackdrop:
      "bg-gradient-to-tr from-primary-500/50 via-secondary-500/50 to-surface-500/50",
    width: "w-[280px] md:w-[480px]",
    padding: "p-4",
    rounded: "rounded-xl",
  };
  function drawerOpen(): void {
    drawerStore.open(drawerSettings);
  }
  function drawerClose(): void {
    drawerStore.close();
  }

  // $: classesActive = (href: string) => (href === $page.url.pathname ? '!variant-filled-primary' : '');
    // Fix SvelteKit scrolling issue
//     import { browser } from "$app/environment";
//     import { afterNavigate, beforeNavigate } from "$app/navigation";

// beforeNavigate(async (nav) => {
//   if (!browser) return;
//   document.getElementsByTagName("html")[0].classList.add("pageSwitch");
// })
// afterNavigate(async (nav) => {
//   if (!browser) return;
//   await tick();
//   document.getElementsByTagName("html")[0].classList.remove("pageSwitch");
// });


///////////////////  NAV FIX \\\\\\\\\\\

import { afterNavigate, beforeNavigate } from "$app/navigation";

let contentDiv: HTMLDivElement;
let topDiv: HTMLDivElement;
import { page } from '$app/stores'; // Import the page store to access the current URL


// beforeNavigate((navigation) => {
//   return new Promise((resolve) => {
//     const transition = document.startViewTransition(async () => {
//       if (contentDiv) {
//         // Fix scroll
//         contentDiv.scrollTop = 0;
//       }
//       // resolve();
//       await navigation.complete;
//     });
//   });
// });

afterNavigate(()=> {
  if ($page.url.pathname === '/') {
    topDiv.scrollIntoView({behavior: 'smooth'})
  } else {
    contentDiv.scrollIntoView({behavior: 'smooth'})
  }
})

 // Function to check if a link is active
 $: currentPath = $page.url.pathname;
 $: isActive = (href: string) => currentPath === href ? 'underline underline-offset-2' : '';

</script>
<style>
  :global(html.pageSwitch) {
    scroll-behavior: smooth;
  }

</style>
<!-- MOBILE MENU -->
<Drawer>
  <nav class="list-nav md:flex">
    <ul class="flex flex-col md:flex-row md:space-x-4 space-y-2 md:space-y-0">
      <li class="hidden md:block"></li>
      <!-- dummy item because 1st list item formats weird -->
      <li>
        <a href="/" on:click={() => drawerClose()} class={isActive('/')}>
          <span class="flex-auto uppercase">Home</span>
        </a>
      </li>
      <li>
        <a href="/about" on:click={() => drawerClose()} class={isActive('/about')}>
          <span class="flex-auto uppercase">About</span>
        </a>
      </li>
      <li>
        <a href="/contact" on:click={() => drawerClose()} class={isActive('/contact')}>
          <span class="flex-auto uppercase">Contact</span>
        </a>
      </li>
      <li>
        <a href="/FAQ" on:click={() => drawerClose()} class={isActive('/FAQ')}>
          <span class="flex-auto uppercase">FAQ</span>
        </a>
      </li>
    </ul>
  </nav>
</Drawer>

<AppShell background='bg-gradient-to-bl from-primary-500/5 via-secondary-500/5 to-surface-500/5' >
  <svelte:fragment slot="header" >
    <AppBar 
      gridcolumns="grid-cols-3"
      slotdefault="place-self-center"
      slottrail="place-content-end"
      background="bg-gradient-to-bl from-primary-500/60 via-secondary-500/30 to-surface-500/5"
      
    >
      <svelte:fragment slot="lead">
        <!-- <img src='images/ASTRA_WHITE_VECTOR.svg' alt='Astra logo'/> -->
        <h1 class="font-bold" >
          <img src='images/ASTRA_COMBO.svg' alt='Astra logo' class='w-[300px]'/>

          <span class=" ">
            <!-- <img src='images/ASTRA_LOGO.svg' alt='Astra logo' class='w-[200px]'/> -->
          <!-- <img src='images/ASTRA_TEXT.svg' alt='Astra logo' class='w-[300px]'/> -->
        </span>
  
          <!-- <a href="/">Astra Injury Rehabilitation Specialists</a> -->
        </h1>
      </svelte:fragment>


      <svelte:fragment slot="trail">
        <!-- Hamburger Button for Small Screens -->
        <button
          class="md:hidden text-xl"
          on:click={drawerOpen}
          aria-label="Toggle Menu"
        >
          <i class="fa-solid fa-bars"></i>
        </button>

        <!-- Navigation Menu -->
        <nav class={`list-nav hidden md:flex`}>
          <ul
            class="flex flex-col md:flex-row md:space-x-4 space-y-2 md:space-y-0"
          >
            <li></li>
            <!-- dummy item because 1st list item formats weird -->
            <li>
              <a href="/" class={isActive('/')}>
                <span class="flex-auto uppercase">Home</span>
              </a>
            </li>
            <li>
              <a href="/about" class={isActive('/about')}>
                <span class="flex-auto uppercase">About</span>
              </a>
            </li>
            <li>
              <a href="/contact" class={isActive('/contact')}>
                <span class="flex-auto uppercase">Contact</span>
              </a>
            </li>
            <li>
              <a href="/FAQ" class={isActive('/FAQ')}>
                <span class="flex-auto uppercase">FAQ</span>
              </a>
            </li>
          </ul>
        </nav>
      </svelte:fragment>
    </AppBar>
  </svelte:fragment>

  <!-- (sidebarLeft) -->
  <!-- (sidebarRight) -->
  <!-- (pageHeader) -->
  <!-- Router Slot -->
   <div bind:this={topDiv}></div>
  <CarouselCombo />
  <div class="container mx-auto px-2 md:p-4 space-y-8  scrollTo" bind:this={contentDiv}>
    <slot></slot>
  </div>
  <!-- ---- / ---- -->
  <!-- (pageFooter) -->
  <svelte:fragment slot="pageFooter">
    <div class="w-screen mx-auto pt-8 space-y-2 bg-surface-100">
      <div class="container mx-auto">
        <div
          class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 place-items-center text-sm"
        >
          <span class="font-bold">Astra Injury Rehabilitation Specialists</span>
          <span
            ><a href="https://maps.app.goo.gl/3d7W2bJQqDQMCPjE6"
              >209 Saint Louis Ave, Fort Worth, TX 76104</a
            ></span
          >
          <span><a href="tel:817-897-5190">817-897-5190</a></span>
          <span
            ><a href="mailto:kdeosarran@astra-consultants.com"
              >kdeosarran@astra-consultants.com</a
            ></span
          >
        </div>

        <div class="text-center py-8 pb-8">
          <h6 class="h6 text-sm">
            Copyright © 2024 Astra Injury Rehabilitation Specialists
            <br />
            Design:
            <a href="https://www.github.com/tylersernett">Tyler Johnson</a>
          </h6>
        </div>
      </div>
    </div>
  </svelte:fragment>
</AppShell>
