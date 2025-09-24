<script lang="ts">
  import Icon from "@iconify/svelte";
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { fade } from "svelte/transition";
  import { page } from "$app/stores"; 
  import CV from "../components/CV.pdf";
  import avatar from "../images/Avatar3.png"

  export let menuOpen: boolean;
  const dispatch = createEventDispatcher();
  let isMobileView = false;
  let currentPath = "";

  // Update currentPath when $page store changes
  $: currentPath = $page.url.pathname.endsWith('/')
    ? $page.url.pathname.slice(0, -1) // Remove trailing slash
    : $page.url.pathname;

    
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

  function handleDownload() {
    const link = document.createElement("a");
    link.href = CV;
    link.setAttribute("download", "CV.pdf"); // Replace with the desired filename
    link.click();
  }
</script>

<!-- HTML -->
<nav class="mt-[0.5rem] sm:mt-[0.5rem] md:mt-[1rem]">
  <div class="max-w-full mx-auto px-4 sm:px-6 lg:px-16">
    <div class="flex items-center justify-between h-16 sm:h-20 lg:h-20">
      <div class="flex-shrink-0">
        <!-- Logo -->
        <a href="/">
          <img 
            src={avatar}
            alt="Logo" 
            class="h-12 w-12 sm:h-14 sm:w-14 lg:h-16 lg:w-16 rounded-full object-cover hover:scale-110 transition-transform duration-300 ease-in-out"
          />
        </a>
      </div>

      <!-- Navbar button -->
      {#if isMobileView && !menuOpen}
        <div class="md:hidden mt-[0.3rem]">
          <button on:click={toggleMenu}>
            <Icon
              icon="line-md:close-to-menu-alt-transition"
              class="text-white cursor-pointer text-3xl sm:text-3xl"
            />
          </button>
        </div>
      {:else}
        <div class="md:hidden mt-[0.3rem]">
          <button on:click={toggleMenu}>
            <Icon
              icon="line-md:menu-to-close-alt-transition"
              class="text-white cursor-pointer text-3xl sm:text-3xl"
            />
          </button>
        </div>
      {/if}

      <!-- Navbar (Bigger screens) -->
      <div class="hidden md:block">
        <div class="ml-10 flex items-baseline space-x-4">
          <a href="/projects/" 
          class={`${
            currentPath === "/projects" 
            ? "border-b-4 border-blue-500 text-gray-200" 
            : "text-gray-300 hover:text-gray-200"
          } font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
         projects
       </a>
       
       <a href="/about/" 
          class={`${
            currentPath === "/about" 
            ? "border-b-4 border-blue-500 text-gray-200" 
            : "text-gray-300 hover:text-gray-200"
          } font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
         about
       </a>
       
       <a href="/contact/" 
          class={`${
            currentPath === "/contact" 
            ? "border-b-4 border-blue-500 text-gray-200" 
            : "text-gray-300 hover:text-gray-200"
          } font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
         contact
       </a>
        </div>
      </div>

      <!-- Reach me button -->
      <div class="hidden md:block mt-[1rem]">
        <button class="btn-cssbuttons flex flex-row items-center">
          <span class="text-gray-200 font-mono font-bold text-xl">reach me</span
          ><span />
          <ul>
            <li>
              <a
                href="https://docs.google.com/document/d/1-uH3fALtNXvl1HbSjqLyRce0pkWXDjvO-Lg_kum4K_I/edit?usp=sharing" 
                class="text-white font-bold text-2xl"
                target="_blank" rel="noopener noreferrer"
                ><Icon icon="pepicons-pop:cv" /></a
              >
            </li>
            <li>
              <a
                href="https://mail.google.com/mail/?view=cm&fs=1&to=damilolaoyeniyi13@gmail.com"
                class="text-white font-bold text-2xl"
                target="_blank" rel="noopener noreferrer"
                ><Icon icon="bxl:gmail" /></a
              >
            </li>
            <li>
              <a
                href="https://www.linkedin.com/in/dami-oyeniyi-97805b23a/"
                class="text-white font-bold text-[1.4rem]"
                target="_blank" rel="noopener noreferrer"
              >
                <Icon icon="uiw:linkedin" />
              </a>
            </li>
          </ul>
        </button>
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
            <div class="flex flex-col gap-[2rem] items-center mt-[4rem]  justify-center">
              <a href="/"
              class={`${
                currentPath === "" || currentPath === "/" 
                ? "border-b-2 border-blue-500 text-white" 
                : "text-gray-300 hover:text-white"
              } block font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
             home
           </a>
              <a href="/projects/"
              class={`${
                currentPath === "/projects" 
                ? "border-b-2 border-blue-500 text-white" 
                : "text-gray-300 hover:text-white"
              } block font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
             projects
           </a>
         
           <a href="/about/"
              class={`${
                currentPath === "/about" 
                ? "border-b-2 border-blue-500 text-white" 
                : "text-gray-300 hover:text-white"
              } block font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
             about
           </a>
         
           <a href="/contact/"
              class={`${
                currentPath === "/contact" 
                ? "border-b-2 border-blue-500 text-white" 
                : "text-gray-300 hover:text-white"
              } block font-mono text-bounce transition duration-500 ease-in-out px-3 py-2 text-2xl font-semibold`}>
             contact
           </a>
            </div>
            <div />
          </div>

            <div class="absolute bottom-4 w-full flex justify-center">
            <h1 class="text-[white] block font-mono text-bounce px-3 py-2 text-2xl font-semibold">dami oyeniyi</h1>
            </div>
        </div>
      </div>
    </div>
  {/if}
{/if}


<!-- CSS -->
<style>
  a.active {
    border-bottom: 4px solid #3bc26a;
    color: #3bc26a;
  }

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