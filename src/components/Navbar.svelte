<!-- JAVASCRIPT -->
<script lang="ts">
  // imports
  import Icon from "@iconify/svelte";
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";
  import { fade, fly } from "svelte/transition";
  import { goto } from "$app/navigation";

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
              <a href="https://twitter.com/SumethWrrn"
                ><svg
                  height="18"
                  width="18"
                  xmlns="http://www.w3.org/2000/svg"
                  version="1.1"
                  viewBox="0 0 1024 1024"
                  class="icon"
                >
                  <path
                    fill="white"
                    d="M962.267429 233.179429q-38.253714 56.027429-92.598857 95.451429 0.585143 7.972571 0.585143 23.990857 0 74.313143-21.723429 148.260571t-65.974857 141.970286-105.398857 120.32-147.456 83.456-184.539429 31.158857q-154.843429 0-283.428571-82.870857 19.968 2.267429 44.544 2.267429 128.585143 0 229.156571-78.848-59.977143-1.170286-107.446857-36.864t-65.170286-91.136q18.870857 2.852571 34.889143 2.852571 24.576 0 48.566857-6.290286-64-13.165714-105.984-63.707429t-41.984-117.394286l0-2.267429q38.838857 21.723429 83.456 23.405714-37.741714-25.161143-59.977143-65.682286t-22.308571-87.990857q0-50.322286 25.161143-93.110857 69.12 85.138286 168.301714 136.265143t212.260571 56.832q-4.534857-21.723429-4.534857-42.276571 0-76.580571 53.979429-130.56t130.56-53.979429q80.018286 0 134.875429 58.294857 62.317714-11.995429 117.174857-44.544-21.138286 65.682286-81.115429 101.741714 53.174857-5.705143 106.276571-28.598857z"
                  /></svg
                ></a
              >
            </li>
            <li>
              <a href="https://codepen.io/sharpth"
                ><svg
                  height="18"
                  width="18"
                  xmlns="http://www.w3.org/2000/svg"
                  version="1.1"
                  viewBox="0 0 1024 1024"
                  class="icon"
                >
                  <path
                    fill="white"
                    d="M123.52064 667.99143l344.526782 229.708899 0-205.136409-190.802457-127.396658zM88.051421 585.717469l110.283674-73.717469-110.283674-73.717469 0 147.434938zM556.025711 897.627196l344.526782-229.708899-153.724325-102.824168-190.802457 127.396658 0 205.136409zM512 615.994287l155.406371-103.994287-155.406371-103.994287-155.406371 103.994287zM277.171833 458.832738l190.802457-127.396658 0-205.136409-344.526782 229.708899zM825.664905 512l110.283674 73.717469 0-147.434938zM746.828167 458.832738l153.724325-102.824168-344.526782-229.708899 0 205.136409zM1023.926868 356.00857l0 311.98286q0 23.402371-19.453221 36.566205l-467.901157 311.98286q-11.993715 7.459506-24.57249 7.459506t-24.57249-7.459506l-467.901157-311.98286q-19.453221-13.163834-19.453221-36.566205l0-311.98286q0-23.402371 19.453221-36.566205l467.901157-311.98286q11.993715-7.459506 24.57249-7.459506t24.57249 7.459506l467.901157 311.98286q19.453221 13.163834 19.453221 36.566205z"
                  /></svg
                ></a
              >
            </li>
            <li>
              <a href="https://github.com/SharpTH">
                <!-- CHANGE THIS TO NORMAL ICONS -->
                <svg
                  height="18"
                  width="18"
                  xmlns="http://www.w3.org/2000/svg"
                  version="1.1"
                  viewBox="0 0 1024 1024"
                  class="icon"
                >
                  <path
                    fill="white"
                    d="M950.930286 512q0 143.433143-83.748571 257.974857t-216.283429 158.573714q-15.433143 2.852571-22.601143-4.022857t-7.168-17.115429l0-120.539429q0-55.442286-29.696-81.115429 32.548571-3.437714 58.587429-10.313143t53.686857-22.308571 46.299429-38.034286 30.281143-59.977143 11.702857-86.016q0-69.12-45.129143-117.686857 21.138286-52.004571-4.534857-116.589714-16.018286-5.12-46.299429 6.290286t-52.589714 25.161143l-21.723429 13.677714q-53.174857-14.848-109.714286-14.848t-109.714286 14.848q-9.142857-6.290286-24.283429-15.433143t-47.689143-22.016-49.152-7.68q-25.161143 64.585143-4.022857 116.589714-45.129143 48.566857-45.129143 117.686857 0 48.566857 11.702857 85.723429t29.988571 59.977143 46.006857 38.253714 53.686857 22.308571 58.587429 10.313143q-22.820571 20.553143-28.013714 58.88-11.995429 5.705143-25.746286 8.557714t-32.548571 2.852571-37.449143-12.288-31.744-35.693714q-10.825143-18.285714-27.721143-29.696t-28.306286-13.677714l-11.410286-1.682286q-11.995429 0-16.603429 2.56t-2.852571 6.582857 5.12 7.972571 7.460571 6.875429l4.022857 2.852571q12.580571 5.705143 24.868571 21.723429t17.993143 29.110857l5.705143 13.165714q7.460571 21.723429 25.161143 35.108571t38.253714 17.115429 39.716571 4.022857 31.744-1.974857l13.165714-2.267429q0 21.723429 0.292571 50.834286t0.292571 30.866286q0 10.313143-7.460571 17.115429t-22.820571 4.022857q-132.534857-44.032-216.283429-158.573714t-83.748571-257.974857q0-119.442286 58.88-220.306286t159.744-159.744 220.306286-58.88 220.306286 58.88 159.744 159.744 58.88 220.306286z"
                  /></svg
                ></a
              >
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
      <div class="w-full h-full md:w-64 bg-[black]">
        <div class="block md:hidden">
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
    border: 2px solid #9fd8e5;
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
