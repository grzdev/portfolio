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
<nav class="mt-[0.5rem] sm:mt-[0.5rem] md:mt-[1rem]">
  <div class="max-w-full mx-auto px-4 sm:px-6 lg:px-16">
    <div class="flex items-center justify-between h-16 sm:h-20 lg:h-20">
      <div class="flex-shrink-0">
        <!-- Logo -->
        <span
          class="text-white text-3xl sm:text-4xl font-bold font-mono lg:text-4xl"
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
            class="text-gray-300 font-mono hover:text-white text-bounce px-3 py-2 rounded-md text-2xl font-semibold"
            >home</a
          >
          <a
            href="/projects"
            class="text-gray-300 font-mono hover:text-white text-bounce px-3 py-2 rounded-md text-2xl font-semibold"
            >projects</a
          >
          <a
            href="/about"
            class="text-gray-300 font-mono hover:text-white text-bounce px-3 py-2 rounded-md text-2xl font-semibold"
            >about</a
          >
          <a
            href="/contact"
            class="text-gray-300 font-mono hover:text-white text-bounce px-3 py-2 rounded-md text-2xl font-semibold"
            >contact</a
          >
        </div>
      </div>

      <!-- Reach me button -->
      <div class="hidden md:block mt-[1rem]">
        <button class="btn-cssbuttons">
          <span class="text-gray-200 font-mono font-bold text-xl">reach me</span
          ><span />
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
                href="/"
                class="text-gray-300 font-mono hover:text-white mt-[3rem] px-3 py-2 rounded-md text-3xl sm:text-4xl font-semibold"
                in:fly={{ y: 200, duration: 700 }}
                out:fly={{ y: 200, duration: 2000 }}>home</a
              >
              <a
                href="/projects"
                class="text-gray-300 font-mono hover:text-white px-3 py-2 rounded-md text-3xl sm:text-4xl font-semibold"
                in:fly={{ y: 200, duration: 1000 }}
                out:fly={{ y: 200, duration: 1500 }}>projects</a
              >
              <a
                href="/about"
                class="text-gray-300 font-mono hover:text-white px-3 py-2 rounded-md text-3xl sm:text-4xl font-semibold"
                in:fly={{ y: 200, duration: 1300 }}
                out:fly={{ y: 200, duration: 1000 }}>about</a
              >
              <a
                href="/contact"
                class="text-gray-300 font-mono hover:text-white px-3 py-2 rounded-md text-3xl sm:text-4xl font-semibold"
                in:fly={{ y: 200, duration: 1600 }}
                out:fly={{ y: 200, duration: 500 }}>contact</a
              >
            </div>
            <div class="mt-[4rem] flex flex-row gap-[2rem]">
              <button
                class="downloadCV"
                in:fly={{ y: 200, duration: 1900 }}
                out:fly={{ y: 200, duration: 300 }}>Get CV</button
              >
              <button
                class="downloadCV2"
                in:fly={{ y: 200, duration: 1900 }}
                out:fly={{ y: 200, duration: 300 }}>Hire me</button
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
    padding: 10px 32px;
    font-weight: 600;
    font-size: 16px;
    line-height: 1;
    color: white;
    background: none;
    border: 2px solid #76c3ff;
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
  .downloadCV {
    appearance: none;
    background-color: transparent;
    border: 0.125em solid #245da1;
    border-radius: 1rem 0 1rem 0;
    box-sizing: border-box;
    color: #65abff;
    cursor: pointer;
    display: inline-block;
    font-family: Roobert, -apple-system, BlinkMacSystemFont, "Segoe UI",
      Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji",
      "Segoe UI Symbol";
    font-size: 16px;
    font-weight: 700;
    line-height: normal;
    margin: 0;
    min-height: 3em;
    min-width: 0;
    outline: none;
    padding: 0.6em 1.5em;
    text-align: center;
    text-decoration: none;
    transition: all 300ms cubic-bezier(0.23, 1, 0.32, 1);
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
    will-change: transform;
  }

  .downloadCV:disabled {
    pointer-events: none;
  }

  .downloadCV:hover {
    color: #fff;
    background-color: #245da1;
    box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px;
    transform: translateY(-2px);
  }

  .downloadCV:active {
    box-shadow: none;
    transform: translateY(0);
  }

  .downloadCV2 {
    appearance: none;
    background-color: #245da1;
    border: 0.125em solid #245da1;
    border-radius: 1rem 0 1rem 0;
    box-sizing: border-box;
    color: white;
    cursor: pointer;
    display: inline-block;
    font-family: Roobert, -apple-system, BlinkMacSystemFont, "Segoe UI",
      Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji",
      "Segoe UI Symbol";
    font-size: 16px;
    font-weight: 700;
    line-height: normal;
    margin: 0;
    min-height: 3em;
    min-width: 0;
    outline: none;
    padding: 0.6em 1.5em;
    text-align: center;
    text-decoration: none;
    transition: all 300ms cubic-bezier(0.23, 1, 0.32, 1);
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
    will-change: transform;
  }

  .downloadCV2:disabled {
    pointer-events: none;
  }

  .downloadCV2:hover {
    color: #65abff;
    background-color: transparent;
    box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px;
    transform: translateY(-2px);
  }

  .downloadCV2:active {
    box-shadow: none;
    transform: translateY(0);
  }
</style>
