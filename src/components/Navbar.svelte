<!-- JAVASCRIPT -->
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

<!-- HTML -->
<nav class="">
  <div class="max-w-full mx-auto px-4 sm:px-6 lg:px-16">
    <div class="flex items-center justify-between h-16 sm:h-20 lg:h-20">
      <div class="flex-shrink-0">
        <!-- Logo -->
        <span
          class="text-white text-3xl sm:text-4xl font-bold font-sans lg:text-4xl"
          >grz.</span
        >
      </div>

      <!-- Navbar button -->
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

      <!-- Navbar (Bigger sccreens) -->
      <div class="hidden md:block">
        <div class="ml-10 flex items-baseline space-x-4">
          <a
            href="/"
            class="text-gray-300 hover:text-white text-bounce px-3 py-2 rounded-md text-xl font-medium"
            >home</a
          >
          <a
            href="/projects"
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

      <!-- Contact me button -->
      <div class="hidden md:block mt-[1rem]">
        <button class="btn-cssbuttons">
          <span class="text-gray-200">Reach me</span><span />
          <ul>
            <li>
              <a
                href="https://twitter.com/grzdev_"
                class="text-white font-bold text-2xl"
                ><Icon icon="bi:twitter" /></a
              >
            </li>
            <li>
              <a
                href="mailto:damilolaoyeniyi13@gmail.com"
                class="text-white font-bold text-2xl"
                ><Icon icon="bxl:gmail" /></a
              >
            </li>
            <li>
              <a
                href="https://github.com/grzdev"
                class="text-white font-bold text-2xl"
              >
                <!-- CHANGE THIS TO NORMAL ICONS -->
                <Icon icon="teenyicons:github-solid" />
              </a>
            </li>
          </ul></button
        >
      </div>
    </div>
  </div>
</nav>

<!-- Sidebar content -->
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
      <div
        class="w-full h-full md:w-64 bg-[black]"
        in:fade={{ duration: 500 }}
        out:fade={{ duration: 700 }}
      >
        <div class="block md:hidden">
          <div class="flex flex-col gap-[2rem] items-center justify-center">
            <div class="flex flex-col gap-[2rem] items-center justify-center">
              <a
                href="#"
                class="text-gray-300 hover:text-white mt-[3rem] px-3 py-2 rounded-md text-3xl sm:text-4xl font-medium"
                in:fly={{ y: 200, duration: 1000 }}
                out:fly={{ y: 200, duration: 2000 }}>home</a
              >
              <a
                href="/projects"
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
              <a
                href="#"
                class="text-gray-300 hover:text-white px-3 py-2 rounded-md text-3xl sm:text-4xl font-medium"
                in:fly={{ y: 200, duration: 2500 }}
                out:fly={{ y: 200, duration: 500 }}>reach me</a
              >
            </div>
            <div />
          </div>
        </div>
      </div>
    </div>
  {/if}
{/if}

<!-- CSS -->
<style>
  .text-bounce {
    transition: transform 0.2s ease-in-out;
  }

  .text-bounce:hover {
    transform: scale(1.1);
  }
  .btn-cssbuttons {
    --btn-color: black;
    position: relative;
    padding: 16px 32px;
    font-family: Roboto, sans-serif;
    font-weight: 600;
    font-size: 16px;
    line-height: 1;
    color: white;
    background: none;
    border: 2px solid #25afce;
    border-radius: 1rem 0 1rem 0;
    outline: none;
    overflow: hidden;
    cursor: pointer;
    /* filter: drop-shadow(0 2px 8px rgba(255, 255, 255, 0.32)); */
    transition: 0.3s cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  .btn-cssbuttons::before {
    position: absolute;
    content: "";
    top: 0;
    left: 0;
    z-index: -1;
    width: 100%;
    height: 100%;
    background: var(--btn-color);
    border-radius: 24px;
    transition: 0.3s cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  .btn-cssbuttons span,
  .btn-cssbuttons span span {
    display: inline-flex;
    vertical-align: middle;
    transition: 0.3s cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  .btn-cssbuttons span {
    transition-delay: 0.05s;
  }

  .btn-cssbuttons span:first-child {
    padding-right: 7px;
  }

  .btn-cssbuttons span span {
    margin-left: 8px;
    transition-delay: 0.1s;
  }

  .btn-cssbuttons ul {
    position: absolute;
    top: 50%;
    left: 0;
    right: 0;
    display: flex;
    margin: 0;
    padding: 0;
    list-style-type: none;
    transform: translateY(-50%);
  }

  .btn-cssbuttons ul li {
    flex: 1;
  }

  .btn-cssbuttons ul li a {
    display: inline-flex;
    vertical-align: middle;
    transform: translateY(55px);
    transition: 0.3s cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  .btn-cssbuttons ul li a:hover {
    opacity: 0.5;
  }

  .btn-cssbuttons:hover::before {
    transform: scale(1.2);
  }

  .btn-cssbuttons:hover span,
  .btn-cssbuttons:hover span span {
    transform: translateY(-55px);
  }

  .btn-cssbuttons:hover ul li a {
    transform: translateY(0);
  }

  .btn-cssbuttons:hover ul li:nth-child(1) a {
    transition-delay: 0.15s;
  }

  .btn-cssbuttons:hover ul li:nth-child(2) a {
    transition-delay: 0.2s;
  }

  .btn-cssbuttons:hover ul li:nth-child(3) a {
    transition-delay: 0.25s;
  }
</style>
