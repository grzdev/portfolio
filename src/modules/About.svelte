<!-- Javascript -->
<script>
  import { onMount } from "svelte";
  import Avatar from "../images/Avatar2.png";
  import { fade, fly } from "svelte/transition";
</script>

<div
  class="flex justify-center items-center flex-col sm:flex-col md:flex-row mt-[1rem] sm:mt-[1rem] md:mt-[3rem] gap-[8rem] sm:gap-[8rem] md:gap-[12rem]"
>
  <div
    class=" flex justify-center items-center flex-col fade-transition"
    in:fade={{ duration: 800 }}
  >
    <img
      src={Avatar}
      alt=""
      class="rounded-full w-[8rem] sm:w-[13rem] md:w-[13rem] mt-[] sm:mt-[] md:mt-[-4rem]"
    />
    <h1
      class="text-4xl sm:text-5xl md:text-5xl text-gray-200 font-mono font-bold mt-[0.5rem] sm:mt-[2rem] md:mt-[2rem]"
    >
      Dami
    </h1>
    <h1
      class="text-4xl sm:text-5xl md:text-5xl text-gray-200 font-mono font-bold"
    >
      Oyeniyi
    </h1>
  </div>
  <!-- <div class="w-[30rem] h-[20rem] bg-white" /> -->
  <div
    class=" move-container mt-[-6rem] sm:mt-[-5rem] md:mt-[1rem] mb-[3rem] sm:mb-[3rem] md:mb-[]"
    transition:fly={{ y: "100%", duration: 1000 }}
  >
    <div class="flip-card">
      <div class="flip-front justify-center items-center flex flex-col">
        <p
          class="text-gray-200 text-lg sm:text-xl md:text-xl mt-[-4rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I started developing websites in March 2022, and to be honest, I'm
          proud of how far I've come in such a short space of time. I pick
          things up quickly and go out of my way to make my work stand out. <br
          /> <br />I believe the design of a site is as important as the
          funtionality, what’s the use of a site being functional if it’s not
          easy to use and vice versa.
        </p>
      </div>
      <div
        class="flip-back justify-center items-center flex flex-col gap-[2rem]"
      >
        <h1>back</h1>
      </div>
    </div>
  </div>
</div>

<style>
  .flip-card {
    position: relative;
    width: 37rem;
    height: 32rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  @media (max-width: 640px) {
    /* Set different width and height for smaller screens */
    .flip-card {
      width: 20rem;
      height: 38rem;
    }
  }

  .flip-container:hover .flip-card {
    transform: rotateY(-180deg);
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
</style>
