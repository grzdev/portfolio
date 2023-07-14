<script>
  import Icon from "@iconify/svelte";
  import Image from "../images/together.png";
  import { fade } from "svelte/transition";
</script>

<div
  class="flex flex-col sm:flex-col md:flex-row text-white justify-center items-center mt-[1rem] sm:mt-[] md:mt-[4rem] gap-[-1rem] sm:gap-[1rem] md:gap-[4rem]"
>
  <div class="flex justify-center items-center flex-col">
    <img
      src={Image}
      alt=""
      class="w-[15rem] sm:w-[25rem] md:w-[27rem]"
      in:fade
    />
    <h1
      class="text-3xl sm:text-5xl md:text-5xl font-bold font-mono w-[20rem] sm:w-[35rem] md:w-[35rem] text-center mt-[1rem]"
    >
      Let's make great stuff together!
    </h1>
    <h1
      class="text-md sm:text-xl md:text-xl font-semibold font-mono w-[18rem] sm:w-[35rem] md:w-[30rem] text-center mt-[1rem]"
    >
      Don't hesitate to get in touch with me if you wish to share ideas or
      collaborate on a project.
    </h1>
  </div>
  <div
    class="flex flex-col mt-[1.8rem] mb-[3rem] sm:mb-[3rem] md:mb-[0rem] move-container"
  >
    <div class="flip-card">
      <div class="flip-front justify-center items-center flex flex-col">
        <div
          class="w-[20rem] sm:w-[30rem] md:w-[30rem] gap-[2rem] mt-[-2rem] flex flex-wrap justify-center items-center"
        >
          <a href="">
            <button class="">
              <span class="text-sm"> gmail </span>
            </button>
          </a>
          <a href="">
            <button class="">
              <span class="text-sm"> twitter </span>
            </button>
          </a>
          <a href="">
            <button class="">
              <span class="text-sm"> linkedin </span>
            </button>
          </a>
          <a href="">
            <button class="">
              <span class="text-sm"> github </span>
            </button>
          </a>
          <a href="">
            <button class="">
              <span class="text-sm"> instagram </span>
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
    height: 23rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  @media (max-width: 640px) {
    /* Set different width and height for smaller screens */
    .flip-card {
      width: 21rem;
      height: 25rem;
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
