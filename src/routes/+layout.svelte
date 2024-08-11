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
  <svelte:fragment slot="footer">
    <div class="w-screen mx-auto pt-8 space-y-2 bg-surface-100">
      <div class="container mx-auto">
        <div
          class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 place-items-center text-sm"
        >
          <span class='font-bold'>Astra Injury Rehabilitation Specialists</span>
          <span>209 Saint Louis Ave, Fort Worth, TX 76104</span>
          <span>817-897-5190</span>
          <span>kdeosarran@astra-consultants.com</span>
        </div>

        <div class="text-center py-8 pb-8">
          <h6 class="h6 text-sm ">
            Copyright © 2024 Astra Injury Rehabilitation Specialists
          </h6>
        </div>
      </div>
    </div>
  </svelte:fragment>
</AppShell>
