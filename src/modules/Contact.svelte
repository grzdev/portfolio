<script>
  import Icon from "@iconify/svelte";
  import Image from "../images/together.png";
  import { fade, fly } from "svelte/transition";
</script>

<div
  class="flex flex-col sm:flex-col md:flex-col text-gray-200 justify-center items-center mt-[1rem] sm:mt-[] md:mt-[1rem] gap-[-1rem] sm:gap-[1rem] md:gap-[1rem]"
>
  <div class="flex justify-center items-center flex-col">
    <h1
      in:fade
      class="text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out text-2xl sm:text-5xl md:text-5xl font-bold font-mono w-[20rem] sm:w-[35rem] md:w-[35rem] text-center mt-[1rem]"
    >
      let's make great stuff together!
    </h1>
  </div>
  <div
    class="flex flex-col mt-[2rem] sm:mt-[1rem] md:mt-[1rem] mb-[3rem] sm:mb-[3rem] md:mb-[0rem] move-container"
  >
    <div class="flip-card" transition:fly={{ y: "100%", duration: 1000 }}>
      <div class="flip-front justify-center items-center flex flex-col">
        <h1
          class="text-gray-200 text-sm sm:text-xl md:text-xl mt-[-2rem] sm:mt-[-2rem] md:mt-[-3rem] font-mono font-bold text-center w-[17rem] sm:w-[25rem] md:w-[25rem]"
        >
          feel free to get in touch with me on my socials if you wish to work
          together.
        </h1>
        <div
          class="w-[14rem] sm:w-[25rem] md:w-[25rem] gap-[2rem] mt-[2rem] flex flex-wrap justify-center items-center"
        >
          <a href="mailto:damilolaoyeniyi13@gmail.com">
            <button class="">
              <span>
                <!-- gmail  -->
                <Icon icon="simple-icons:gmail" />
              </span>
            </button>
          </a>
          <a href="https://twitter.com/grzdev_">
            <button class="">
              <span>
                <!-- twitter  -->
                <Icon icon="icon-park-twotone:big-x" />
              </span>
            </button>
          </a>
          <a href="https://www.linkedin.com/in/damilola-oyeniyi-97805b23a/">
            <button class="">
              <span>
                <!-- linkedin  -->
                <Icon icon="fa:linkedin" />
              </span>
            </button>
          </a>
          <a href="https://github.com/grzdev">
            <button class="">
              <span>
                <!-- github  -->
                <Icon icon="teenyicons:github-solid" />
              </span>
            </button>
          </a>
          <a href="https://www.instagram.com/grzdev_/">
            <button class="">
              <span>
                <!-- instagram  -->
                <Icon icon="teenyicons:instagram-solid" />
              </span>
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
    height: 28rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  @media (max-width: 640px) {
    /* Set different width and height for smaller screens */
    .flip-card {
      width: 21rem;
      height: 28rem;
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
    width: 6.2em;
    height: 4.2em;
    background-color: #212121;
    border: 0.08em solid #fff;
    border-radius: 2rem;
    font-size: 13px;
    font-family: monospace;
  }

  button span {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: 700;
    bottom: 0.4em;
    width: 3.7em;
    height: 2.2em;
    background: rgb(12, 32, 56);
    background: linear-gradient(
      304deg,
      rgba(12, 32, 56, 1) 0%,
      rgba(57, 167, 254, 1) 100%
    );

    border-radius: 1.4rem;
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
