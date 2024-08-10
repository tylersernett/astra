<script>
  import "../app.css";
  import { AppShell, AppBar } from "@skeletonlabs/skeleton";
</script>

<!-- <nav>
  <a href="/">home</a>
  <a href="/about">about</a>
  <a href="/FAQ">FAQ</a>
  <a href="/contact">contact</a>
</nav> -->

<AppShell>
  <svelte:fragment slot="header">
    <AppBar
      gridcolumns="grid-cols-3"
      slotdefault="place-self-center"
      slottrail="place-content-end"
    >
      <svelte:fragment slot="lead">(icon)</svelte:fragment>
      Astra Injury Rehabilitation Specialists
      <svelte:fragment slot="trail">
        <nav class="list-nav">
          <ul class="flex space-x-4">
            <li>
              <a href="/">
                <span class="w-6 text-center"
                  ><i class="fa-solid fa-home"></i></span
                >
                <span>Home</span>
              </a>
            </li>
            <li>
              <a href="/about">
                <span class="w-6 text-center"
                  ><i class="fa-solid fa-book"></i></span
                >
                <span>About</span>
              </a>
            </li>
            <li>
              <a href="/contact">
                <span class="w-6 text-center"
                  ><i class="fa-solid fa-bullhorn"></i></span
                >
                <span>Contact</span>
              </a>
            </li>
            <li>
              <a href="/FAQ">
                <span class="w-6 text-center"
                  ><i class="fa-solid fa-bullhorn"></i></span
                >
                <span>FAQ</span>
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
  <slot></slot>
  <!-- ---- / ---- -->
  <!-- (pageFooter) -->
  <svelte:fragment slot="pageFooter">
    <div class="container mx-auto p-4 space-y-8">
      <div class="flex justify-center items-center space-x-2">
        <span>Astra Injury Rehabilitation Specialists</span>
        <span>|</span>
        <span>209 Saint Louis Ave, Fort Worth, TX 76104</span>
        <span>|</span>
        <span>817-897-5190</span>
        <span>|</span>
        <span>kdeosarran@astra-consultants.com</span>
      </div>
      <div class="text-center">
        <br />
        Copyright © 2024 Astra Injury Rehabilitation Specialists
      </div>
    </div>
    
  </svelte:fragment>
</AppShell>
