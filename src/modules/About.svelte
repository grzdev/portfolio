<script lang="ts">
  import { onMount } from "svelte";
  import Avatar from "../images/Avatar2.png";
  import { fade, fly } from "svelte/transition";
  import Icon from "@iconify/svelte";

  let fadeIn = false;
  onMount(() => {
    setTimeout(() => {
      fadeIn = true;
    }, 200);
  });

  let flippedCardId: number | null = null; // Track the flipped card
  const toggleFlip = (id: number) => {
    flippedCardId = flippedCardId === id ? null : id;
  };

  const handleKeyDown = (event: KeyboardEvent, id: number) => {
    if (event.key === "Enter" || event.key === " ") {
      toggleFlip(id);
    }
  };
</script>

<div
  class="flex justify-center items-center flex-col sm:flex-col md:flex-row mt-[1rem] sm:mt-[1rem] md:mt-[1rem] gap-[8rem] sm:gap-[8rem] md:gap-[12rem]"
>
  <div class="flex justify-center items-center flex-col fade-transition">
    <img
      src={Avatar}
      in:fade={{ duration: 1500 }}
      alt="Avatar"
      class="rounded-full w-[8rem] sm:w-[13rem] md:w-[13rem] mt-[] sm:mt-[] md:mt-[-1rem]"
    />
    <h1
      in:fade={{ duration: 1500 }}
      class="text-4xl sm:text-5xl md:text-5xl text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out font-mono font-bold mt-[0.5rem] sm:mt-[1rem] md:mt-[1rem]"
    >
      Dami
    </h1>
    <h1
      in:fade={{ duration: 1500 }}
      class="text-4xl sm:text-5xl md:text-5xl text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out font-mono font-bold"
    >
      Oyeniyi
    </h1>
    <div class="hidden md:flex mt-[2rem]">
      <a
        href="https://docs.google.com/document/d/1-uH3fALtNXvl1HbSjqLyRce0pkWXDjvO-Lg_kum4K_I/edit?usp=sharing"
      >
        <button class="mt-[0.5rem]">
          <span class="text-sm">
            resume <Icon icon="ic:sharp-play-arrow" /></span
          >
        </button>
      </a>
    </div>
  </div>

  <div
    class="flip-container move-container mt-[-6rem] sm:mt-[-4rem] md:mt-[1rem]"
    transition:fly={{ y: "100%", duration: 1000 }}
  >
    <div class="flip-card {flippedCardId === 1 ? 'flipped' : ''}" on:click={() => toggleFlip(1)} on:keydown={(e) => handleKeyDown(e, 1)} role="button" tabindex="0" >
      <div class="flip-front justify-center items-center flex flex-col">
        <h1
          class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[-3rem] sm:mt-[-1rem] md:mt-[-3rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I build interactive applications using frontend technology, mainly on
          the web and also on mobile.
        </h1>
        <p
          class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[1rem] md:mt-[2rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I'm self-taught, and i've been building mainly with frontend tech for 2 years. I've also dabbled into ui design with figma, 
          mobile app dev with react native and backend api integration with nodejs.
        </p>
        <p
          class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[1rem] md:mt-[2rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          What separates me is my fixation on providing a seamless yet distinct
          user-centric design.
        </p>
      </div>

      <div
        class="flip-back justify-center items-center flex flex-col gap-[2rem]"
      >
        <h1
          class="text-gray-200 text-xl sm:text-3xl md:text-3xl font-mono font-bold mt-[-2rem] sm:mt-[] md:mt-[]"
        >
          stack
        </h1>
        <div class="grid grid-cols-3 gap-[2rem]">
          <div>
            <Icon
              icon="logos:html-5"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="vscode-icons:file-type-css"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="devicon:tailwindcss"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="skill-icons:javascript"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="devicon:react"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="skill-icons:typescript"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="devicon:svelte"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="logos:nextjs-icon"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon
              icon="devicon:mongodb"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>

          <div>
            <Icon
              icon="devicon:nodejs"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
          <div>
            <Icon icon="bi:github" class="text-4xl sm:text-6xl md:text-6xl" />
          </div>
          <div>
            <Icon
              icon="logos:postman-icon"
              class="text-4xl sm:text-6xl md:text-6xl"
            />
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="flex md:hidden mt-[-7rem] mb-[3rem] sm:mb-[3rem] md:mb-[]">
    <a
      href="https://drive.google.com/file/d/1iqlVhJikyk7iAO9GIPInKJh4ft_wQmgz/view?usp=sharing"
    >
      <button class="mt-[0.5rem]">
        <span class="text-sm"> resume <Icon icon="ic:sharp-play-arrow" /></span>
      </button>
    </a>
  </div>
</div>

<style>
  .flip-card {
    position: relative;
    width: 37rem;
    height: 33rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  .flip-container .flip-card.flipped {
    transform: rotateY(-180deg);
  }

  @media (max-width: 640px) {
    .flip-card {
      width: 20rem;
      height: 27rem;
    }
  }

  .flip-front,
  .flip-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
  }
  .flip-front {
    background-image: url("../images/bg1.jpeg"); /* Move background image to flip-front */
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    border-radius: 1rem 0 1rem 0;
  }

  .flip-back {
    transform: rotateY(180deg);
    background-color: #1a2c50;
    border-radius: 1rem 0 1rem 0;
  }

  .move-container {
    animation: move 2.5s ease-in-out infinite;
  }

  @keyframes move {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-9px);
    }
  }

  button {
    padding: 0.1em 0.25em;
    width:
 11.2em;
    height: 3.7em;
    background-color: #212121;
    border: 0.08em solid #fff;
    border-radius: 1rem 0 1rem 0;
    font-size: 12px;
    font-family: monospace;
  }

  button span {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: 700;
    bottom: 0.4em;
    width: 7em;
    height: 2em;
    background: rgb(12, 32, 56);
    background: linear-gradient(
      304deg,
      rgba(12, 32, 56, 1) 0%,
      rgba(57, 167, 254, 1) 100%
    );

    border-radius: 0.8rem 0 0.8rem 0;
    font-size: 1.5em;
    color: #fff;
    border: 0.08em solid #fff;
    box-shadow: 0 0.4em 0.1em 0.019em #d3d1d1;
  }

  button span:hover {
    transition: all 0.5s;
    transform: translate(0, 0.4em);
    box-shadow: 0 0 0 0 #d3d1d1;
  }

  button span:not(hover) {
    transition: all 1s;
  }
</style>
