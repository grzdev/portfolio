<script lang="ts">
  import { onMount } from "svelte";
  import Avatar from "../images/3dPortraitt2.png";
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
  class="flex justify-center items-center flex-col sm:flex-col md:flex-row mt-[1rem] md:mt-[2rem] md:mb-[2rem] gap-[8rem] sm:gap-[8rem] md:gap-[12rem]"
>
  <div class="flex justify-center items-center flex-col fade-transition">
    <img
      src={Avatar}
      in:fade={{ duration: 1500 }}
      alt="Avatar"
      class="rounded-full w-[12rem] md:w-[15rem] mt-[] sm:mt-[] md:mt-[-1rem]"
    />
    <h1
      in:fade={{ duration: 1500 }}
      class="text-4xl sm:text-5xl md:text-4xl text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out font-mono font-bold mt-[1rem] sm:mt-[1rem] md:mt-[1rem]"
    >
      Dami
    </h1>
    <h1
      in:fade={{ duration: 1500 }}
      class="text-4xl sm:text-5xl md:text-4xl text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out font-mono font-bold"
    >
      Oyeniyi
    </h1>
    <div class="mt-[1rem] md:mt-[1.5rem]">
      <a
        href="https://docs.google.com/document/d/1-uH3fALtNXvl1HbSjqLyRce0pkWXDjvO-Lg_kum4K_I/edit?usp=sharing" target="_blank" rel="noopener noreferrer"
      >
        <button class="mt-[0.9rem] md:mt-[0.5rem] ">
          <span class="flex justify-center items-center gap-[0.5rem]">
            cv <Icon icon="memory:arrow-right" /></span
          >
        </button>
      </a>
    </div>
  </div>

  <div
    class="flip-container move-container mt-[-5rem] sm:mt-[-4rem] md:mt-[1rem] mb-[3rem] md:mb-[0]"
    transition:fly={{ y: "100%", duration: 1000 }}
  >
    <div class="flip-card {flippedCardId === 1 ? 'flipped' : ''}" on:click={() => toggleFlip(1)} on:keydown={(e) => handleKeyDown(e, 1)} role="button" tabindex="0" >
      <div class="flip-front justify-center items-center flex flex-col">
        <h1
          class="text-gray-200 text-sm sm:text-lg md:text-lg mt-[-2rem] sm:mt-[-1rem] md:mt-[-2.2rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I build interactive sites and apps for the web and mobile, with a strong focus on frontend development.
        </h1>
        <p
          class="text-gray-200 text-sm sm:text-lg md:text-lg mt-[1rem] md:mt-[1.2rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I’m self-taught and have spent the past 4 years honing my craft, bringing ideas to life with clean, engaging interfaces.
          Along the way, I’ve explored UI design with Figma, 3D modeling in Blender, and mobile development with React Native.
        </p>
        <p
          class="text-gray-200 text-sm sm:text-lg md:text-lg mt-[1rem] md:mt-[1.2rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          What drives me is a fixation on making design both seamless and beautiful.
        </p>
      </div>

      <div
        class="flip-back justify-center items-center flex flex-col gap-[2rem]"
      >
        <h1
          class="text-gray-200 text-xl sm:text-3xl md:text-2xl font-mono font-bold mt-[-2rem] sm:mt-[] md:mt-[0.2rem]"
        >
          stack
        </h1>
        <div class="grid grid-cols-3 gap-[1rem] md:gap-[2.5rem] gap-y-[2rem] md:sm:gap-y-[0]">
          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="skill-icons:javascript"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">javascript</h1>
          </div>

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="skill-icons:typescript"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">typescript</h1>
          </div>

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="devicon:react"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">react</h1>
          </div>

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="devicon:tailwindcss"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">tailwind</h1>
          </div>  

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="devicon:chakraui" 
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">chakra ui</h1>
          </div>  

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="logos:figma"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">figma</h1>
          </div>  

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="devicon:svelte"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">svelte</h1>
          </div>
           
          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="logos:nextjs-icon"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">next js</h1>
          </div>

          <div class="flex flex-col justify-center items-center gap-[0.5rem] md:gap-[0.6rem]">
            <Icon
              icon="logos:blender"
              class="text-4xl md:text-4xl"
            />
            <h1 class=" text-[0.8rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono">blender</h1>
          </div>

        
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .flip-card {
    position: relative;
    width: 33rem;
    height: 28rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  .flip-container .flip-card.flipped {
    transform: rotateY(-180deg);
  }

  @media (max-width: 640px) {
    .flip-card {
      width: 20rem;
      height: 28rem;
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
 11.7em;
    height: 5em;
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
    width: 5em;
    height: 2em;
    background: rgb(12, 32, 56);
    background: linear-gradient(
      304deg,
      rgba(12, 32, 56, 1) 0%,
      rgba(57, 167, 254, 1) 100%
    );

    border-radius: 0.8rem 0 0.8rem 0;
    font-size: 2.2em;
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
