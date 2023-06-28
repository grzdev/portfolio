<!-- javascript -->
<script lang="ts">
  // imports
  import Icon from "@iconify/svelte";
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { fade, fly } from "svelte/transition";

  //  navbar function
  export let menuOpen: boolean;
  const dispatch = createEventDispatcher();
  let isMobileView = false;

  onMount(() => {
    const checkViewport = () => {
      isMobileView = window.innerWidth <= 768;
    };

    checkViewport();
    window.addEventListener("resize", checkViewport);
  });

  function toggleMenu() {
    menuOpen = !menuOpen;
    dispatch("toggleMenu");
  }

  function handleKeyDown(event: { key: string }) {
    if (event.key === "Escape") {
      toggleMenu();
    }
  }

  //animation
</script>

<!-- html -->
<!-- main div -->
<nav class="">
  <div class="max-w-full mx-auto px-4 sm:px-6 lg:px-16">
    <div class="flex items-center justify-between h-16 sm:h-20 lg:h-20">
      <div class="flex-shrink-0">
        <span class="text-white text-3xl sm:text-4xl lg:text-4xl">grz.</span>
      </div>
      {#if isMobileView && !menuOpen}
        <div class="md:hidden">
          <button on:click={toggleMenu}>
            <Icon
              icon="ci:menu-alt-02"
              class="text-white cursor-pointer text-3xl"
            />
          </button>
        </div>
      {:else}
        <div class="md:hidden">
          <button on:click={toggleMenu}>
            <Icon
              icon="ep:close-bold"
              class="text-white cursor-pointer text-3xl"
            />
          </button>
        </div>
      {/if}
      <div class="hidden md:block">
        <div class="ml-10 flex items-baseline space-x-4">
          <a
            href="#"
            class="text-gray-300 hover:text-white text-bounce px-3 py-2 rounded-md text-xl font-medium"
            >home</a
          >
          <a
            href="#"
            class="text-gray-300 hover:text-white text-bounce px-3 py-2 rounded-md text-xl font-medium"
            >projects</a
          >
          <a
            href="#"
            class="text-gray-300 hover:text-white text-bounce px-3 py-2 rounded-md text-xl font-medium"
            >about</a
          >
        </div>
      </div>
    </div>
  </div>
</nav>

<!-- mobile nav -->
{#if isMobileView}
  {#if menuOpen}
    <div class="fixed inset-0 z-50">
      <div
        class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8"
        on:click={toggleMenu}
        on:keydown={handleKeyDown}
        tabindex="-1"
        role="button"
        aria-label="Close"
      />
      <div class="w-full h-full md:w-64 bg-[black]">
        <!-- Sidebar content goes here -->
        <div class="block md:hidden">
          <div class="flex flex-col gap-[2rem] items-center justify-center">
            <a
              href="#"
              class="text-gray-300 hover:text-white mt-[3rem] px-3 py-2 rounded-md text-3xl sm:text-4xl font-medium"
              in:fly={{ y: 200, duration: 1000 }}
              out:fly={{ y: 200, duration: 2000 }}>home</a
            >
            <a
              href="#"
              class="text-gray-300 hover:text-white px-3 py-2 rounded-md text-3xl sm:text-4xl font-medium"
              in:fly={{ y: 200, duration: 1500 }}
              out:fly={{ y: 200, duration: 1500 }}>projects</a
            >
            <a
              href="#"
              class="text-gray-300 hover:text-white px-3 py-2 rounded-md text-3xl sm:text-4xl font-medium"
              in:fly={{ y: 200, duration: 2000 }}
              out:fly={{ y: 200, duration: 1000 }}>about</a
            >
          </div>
        </div>
      </div>
    </div>
  {/if}
{/if}

<!-- css -->
<style>
  .text-bounce {
    transition: transform 0.2s ease-in-out;
  }

  .text-bounce:hover {
    transform: scale(1.1);
  }
</style>
