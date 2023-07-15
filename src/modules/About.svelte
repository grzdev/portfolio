<!-- Javascript -->
<script>
  import { onMount } from "svelte";
  import Avatar from "../images/Avatar2.png";
  import { fade, fly } from "svelte/transition";
  import Icon from "@iconify/svelte";
</script>

<div
  class="flex justify-center items-center flex-col sm:flex-col md:flex-row mt-[1rem] sm:mt-[1rem] md:mt-[3rem] gap-[8rem] sm:gap-[8rem] md:gap-[12rem]"
>
  <div class=" flex justify-center items-center flex-col fade-transition">
    <img
      src={Avatar}
      in:fade
      alt=""
      class="rounded-full w-[8rem] sm:w-[13rem] md:w-[13rem] mt-[] sm:mt-[] md:mt-[-6rem]"
    />
    <h1
      in:fade
      class="text-4xl sm:text-5xl md:text-5xl text-gray-200 font-mono font-bold mt-[0.5rem] sm:mt-[1rem] md:mt-[1rem]"
    >
      Dami
    </h1>
    <h1
      in:fade
      class="text-4xl sm:text-5xl md:text-5xl text-gray-200 font-mono font-bold"
    >
      Oyeniyi
    </h1>
  </div>
  <!-- <div class="w-[30rem] h-[20rem] bg-white" /> -->
  <div
    class="move-container mt-[-6rem] sm:mt-[-6rem] md:mt-[1rem] mb-[3rem] sm:mb-[3rem] md:mb-[]"
    transition:fly={{ y: "100%", duration: 1000 }}
  >
    <div class="flip-card">
      <div class="flip-front justify-center items-center flex flex-col">
        <h1
          class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[-3rem] sm:mt-[-1rem] md:mt-[-1rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I build eye catching and easy to use interfaces using the latest web
          design tools.
        </h1>
        <p
          class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[1rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          I'm a self taught frontend developer with about two years of
          experience, with my focus in react and typescript.
        </p>
        <p
          class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[1rem] font-mono font-bold text-center w-[17rem] sm:w-[30rem] md:w-[30rem]"
        >
          My obsession with offering a smooth and unique user interface and
          experience is what sets me apart.
        </p>
        <div class="mt-[2.5rem] flex flex-col justify-center items-center">
          <h1
            class="text-gray-200 text-sm sm:text-lg md:text-xl mt-[-1rem] font-mono font-bold text-center"
          >
            Want to know more?
          </h1>
          <a
            href="https://drive.google.com/file/d/1MdLGofZUqaWFCSiHRrUZsooXSRHXBdIo/view?usp=sharing"
          >
            <button class="mt-[0.5rem]">
              <span class="text-sm">
                resume <Icon icon="ic:sharp-play-arrow" /></span
              >
            </button>
          </a>
        </div>
      </div>
    </div>
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

  @media (max-width: 640px) {
    /* Set different width and height for smaller screens */
    .flip-card {
      width: 20rem;
      height: 32rem;
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

  button {
    padding: 0.1em 0.25em;
    width: 11.2em;
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
