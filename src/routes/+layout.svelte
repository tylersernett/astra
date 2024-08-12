<script lang="ts">
  import "../app.css";
  import { AppShell, AppBar } from "@skeletonlabs/skeleton";
  import Carousel from '../lib/components/Carousel.svelte';

  // $: classesActive = (href: string) => (href === $page.url.pathname ? '!variant-filled-primary' : '');
</script>

<AppShell>
  <svelte:fragment slot="header">
    <AppBar
      gridcolumns="grid-cols-3"
      slotdefault="place-self-center"
      slottrail="place-content-end"
    >
      <svelte:fragment slot="lead">(icon)</svelte:fragment>
      <h1 class='font-bold'><a href='/'>Astra Injury Rehabilitation Specialists</a></h1>

      <svelte:fragment slot="trail">
        <nav class="list-nav">
          <ul class="flex space-x-4">
            <li></li><!-- dummy item because 1st list item formats weird -->
            <li>
              <a href="/">
                <span class="flex-auto uppercase">Home</span>
              </a>
            </li>
            <!-- <li>
              <a href={href} class="{classesActive(href)}">Page</a>
            </li> -->
            <li>
              <a href="/about">
                <span class="flex-auto uppercase">About</span>
              </a>
            </li>
            <li>
              <a href="/contact">
                <span class="flex-auto uppercase">Contact</span>
              </a>
            </li>
            <li>
              <a href="/FAQ">
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
  <Carousel/>
  <div class="container mx-auto p-4 space-y-8 pb-16">
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
          <span class='font-bold'>Astra Injury Rehabilitation Specialists</span>
          <span><a href='https://maps.app.goo.gl/3d7W2bJQqDQMCPjE6'>209 Saint Louis Ave, Fort Worth, TX 76104</a></span>
          <span><a href='tel:817-897-5190'>817-897-5190</a></span>
          <span><a href='mailto:kdeosarran@astra-consultants.com'>kdeosarran@astra-consultants.com</a></span>
        </div>

        <div class="text-center py-8 pb-8">
          <h6 class="h6 text-sm ">
            Copyright © 2024 Astra Injury Rehabilitation Specialists
            <br/>
            Design: <a href='https://www.github.com/tylersernett'>Tyler Johnson</a>
          </h6>
        </div>
      </div>
    </div>
  </svelte:fragment>
</AppShell>
