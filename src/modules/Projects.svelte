<!-- Javascript -->
<script lang="ts">
  import ProjectsCard from "../components/ProjectsCard.svelte";
  import type { Project, Project2 } from "../components/projectsInterface";
  import personalProjects from "../components/personalProjects.json";
  import pixelgrab from "../images/pixelgrab.png";
  import yezirPortfolio from "../images/yezir-portfolio.png";
  import testsource from "../images/testsource.png";
  const projectImageMap: Record<number, string> = { 1: pixelgrab, 2: yezirPortfolio, 3: testsource };
  export let projects: Project[] = personalProjects.personal.map((p) => ({ ...p, image: projectImageMap[p.id] }));
  import Donut from "../images/content.jpg";
  import yezir from "../images/yezir3.png";
  import room14 from "../images/4krender.png";
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";
  import Icon from "@iconify/svelte";
  import hackathon1 from "../images/hackathon1.jpg";
  import hackathon2 from "../images/hackthon2.jpg";
  import hackathon4 from "../images/hackathon4.jpg";
  import leapility from "../images/leapility.jpg";

  let showDiv = false;

  onMount(() => {
    showDiv = true;
  });
</script>

<!-- HTML -->
<div
  class="max-w-[90rem] mx-auto flex flex-col px-4 sm:px-6 lg:px-16 xl:px-24 2xl:px-32 mt-[1rem] sm:mt-[1rem] md:mt-[2rem] overflow-x-hidden mb-[3rem] md:mb-[0rem]"
>
  <div class="flex flex-col">
    <h1
      class="text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out text-xl sm:text-3xl md:text-3xl font-mono font-bold"
      in:fade
    >
      some featured work
    </h1>
    <div
      class="flex flex-row mt-[0.3rem] gap-[1.3rem] sm:gap-[2rem] md:gap-[2rem] overflow-x-auto md:overflow-x-visible custom-scrollbar"
      class:slide-in={showDiv}
    >
      <ProjectsCard {projects} />
    </div>
  </div>
  <div class="flex flex-col mt-[1rem] sm:mt-[2rem] md:mt-[1rem] mb-[2rem]">
    <h1
      class="text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out text-xl sm:text-3xl md:text-3xl font-mono font-bold mt-[1rem]"
      in:fade
    >
      some 3d renders
    </h1>
    <div
      class="flex flex-row mt-[0.3rem] gap-[1.3rem] sm:gap-[2rem] md:gap-[2rem] overflow-x-auto md:overflow-x-visible custom-scrollbar"
      class:slide-in3={showDiv}
    >
      <!-- others/> -->
      <div
        class=" move-container mt-[1rem] flex flex-row gap-[1.4rem] md:gap-[2rem] md:w-full"
      >
        <!-- room 14 -->
        <div class="flip-card justify-center items-center flex flex-col">
          <div class="relative">
            <img
              src={room14}
              alt=""
              loading="lazy"
              class="w-[14.5rem] md:w-[17.5rem] rounded-[1rem] mt-[-3rem]"
            />
            <Icon
              icon="logos:blender"
              class="absolute top-[-2.5rem] left-2 text-[1rem] md:text-[1.5rem]"
            />
            <Icon
              icon="skill-icons:instagram"
              class="absolute top-[-2.5rem] right-3 text-[1.1rem] md:text-[1.5rem]"
            />
          </div>
          <div
            class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem] md:gap-[0.4rem]"
          >
            <h1
              class="text-[1.2rem] md:text-[1.6rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono"
            >
              room 14
            </h1>
            <div class="flex flex-row justify-center items-center gap-[2rem]">
              <a
                href="https://www.instagram.com/p/DPG9JWlDIrj/?igsh=MXU5ejZsbjJpZm50OA=="
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
                >
                  <h1>
                    <Icon
                      icon="memory:eye-fill"
                      class="text-[1.3rem] md:text-[1.5rem]"
                    />
                  </h1>
                  <h1
                    class="underline underline-offset-2 text-[1rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono"
                  >
                    instagram
                  </h1>
                </div>
              </a>
              <a
                href="https://www.behance.net/gallery/235695887/room-14"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold cursor-pointer"
                >
                  <h1 class="hd-icon-hover">
                    <Icon
                      icon="material-symbols:hd-outline-rounded"
                      class="text-[1.7rem] md:text-[2rem]"
                    />
                  </h1>
                </div>
              </a>
            </div>
          </div>
        </div>

        <!-- donut -->
        <div class="flip-card justify-center items-center flex flex-col">
          <div class="relative">
            <img
              src={Donut}
              alt=""
              loading="lazy"
              class="w-[14rem] md:w-[16rem] rounded-[1rem] mt-[-3rem]"
            />
            <Icon
              icon="logos:blender"
              class="absolute top-[-2.5rem] left-2 text-[1rem] md:text-[1.5rem]"
            />
            <Icon
              icon="skill-icons:instagram"
              class="absolute top-[-2.5rem] right-3 text-[1.1rem] md:text-[1.5rem]"
            />
          </div>
          <div
            class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem] md:gap-[0.4rem]"
          >
            <h1
              class="text-[1.2rem] md:text-[1.6rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono"
            >
              3d donut
            </h1>

            <div class="flex flex-row justify-center items-center gap-[2rem]">
              <a
                href="https://www.instagram.com/share/BAMGK-fYZ9"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
                >
                  <h1>
                    <Icon
                      icon="memory:eye-fill"
                      class="text-[1.3rem] md:text-[1.5rem]"
                    />
                  </h1>
                  <h1
                    class="underline underline-offset-2 text-[1rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono"
                  >
                    instagram
                  </h1>
                </div>
              </a>
              <a
                href="https://www.behance.net/gallery/235695171/donut"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold cursor-pointer"
                >
                  <h1 class="hd-icon-hover">
                    <Icon
                      icon="material-symbols:hd-outline-rounded"
                      class="text-[1.7rem] md:text-[2rem]"
                    />
                  </h1>
                </div>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="flex flex-col mb-[2rem]">
    <h1
      class="text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out text-xl sm:text-3xl md:text-3xl font-mono font-bold"
      in:fade
    >
      some hackathon wins
    </h1>
    <div
      class="flex flex-row mt-[0.3rem] gap-[1.3rem] sm:gap-[2rem] md:gap-[2rem] overflow-x-auto md:overflow-x-visible custom-scrollbar"
      class:slide-in3={showDiv}
    >
      <div
        class=" move-container mt-[1rem] flex flex-row gap-[1.4rem] md:gap-[2rem] md:w-full"
      >
        <!-- hackathon card 1 -->
        <div
          class="flip-card hackathon-card justify-center items-center flex flex-col"
        >
          <div class="relative">
            <img
              src={hackathon1}
              alt="Hackathon 1"
              loading="lazy"
              class="w-[14.5rem] md:w-[17.5rem] rounded-[1rem] mt-[-3rem]"
            />
          </div>
          <div
            class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem] md:gap-[0.4rem]"
          >
            <h1
              class="text-[1.2rem] md:text-[1.6rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono"
            >
              skillsheet
            </h1>
            <div class="flex flex-row justify-center items-center gap-[1.5rem]">
              <a
                href="https://x.com/Zai_org/status/1960326809515696535?s=20"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div class="trophy-glow cursor-pointer">
                  <Icon
                    icon="noto:trophy"
                    class="text-[2rem] md:text-[2.5rem]"
                  />
                </div>
              </a>
              <a
                href="https://x.com/Zai_org/status/1960326809515696535?s=20"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
                >
                  <h1>
                    <Icon
                      icon="memory:eye-fill"
                      class="text-[1.3rem] md:text-[1.5rem]"
                    />
                  </h1>
                  <h1
                    class="underline underline-offset-2 text-[1rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono"
                  >
                    tweet
                  </h1>
                </div>
              </a>
            </div>
          </div>
        </div>

        <!-- hackathon card 2 - webgrabber -->
        <div
          class="flip-card hackathon-card justify-center items-center flex flex-col"
        >
          <div class="relative">
            <img
              src={hackathon2}
              alt="Webgrabber"
              loading="lazy"
              class="w-[14.5rem] md:w-[17.5rem] rounded-[1rem] mt-[-3rem]"
            />
          </div>
          <div
            class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem] md:gap-[0.4rem]"
          >
            <h1
              class="text-[1.2rem] md:text-[1.6rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono"
            >
              webgrabber
            </h1>
            <div class="flex flex-row justify-center items-center gap-[1.5rem]">
              <a
                href="https://x.com/CreaoAI/status/2018740778680701096?s=20"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div class="trophy-glow cursor-pointer">
                  <Icon
                    icon="noto:trophy"
                    class="text-[2rem] md:text-[2.5rem]"
                  />
                </div>
              </a>
              <a
                href="https://x.com/CreaoAI/status/2018740778680701096?s=20"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
                >
                  <h1>
                    <Icon
                      icon="memory:eye-fill"
                      class="text-[1.3rem] md:text-[1.5rem]"
                    />
                  </h1>
                  <h1
                    class="underline underline-offset-2 text-[1rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono"
                  >
                    tweet
                  </h1>
                </div>
              </a>
            </div>
          </div>
        </div>

        <!-- hackathon card 3 - leapility -->
        <div
          class="flip-card hackathon-card justify-center items-center flex flex-col"
        >
          <div class="relative">
            <img
              src={leapility}
              alt="Leapility"
              loading="lazy"
              class="w-[14.5rem] md:w-[17.5rem] h-[9rem] object-cover object-top rounded-[1rem] mt-[-3rem]"
            />
          </div>
          <div
            class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem] md:gap-[0.4rem]"
          >
            <h1
              class="text-[1.2rem] md:text-[1.6rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono"
            >
              learn from anything
            </h1>
            <div class="flex flex-row justify-center items-center gap-[1.5rem]">
              <a
                href="https://x.com/leapility/status/2039670636805607633?s=20"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div class="trophy-glow cursor-pointer">
                  <Icon
                    icon="noto:trophy"
                    class="text-[2rem] md:text-[2.5rem]"
                  />
                </div>
              </a>
              <a
                href="https://x.com/leapility/status/2039670636805607633?s=20"
                target="_blank"
                rel="noopener noreferrer"
              >
                <div
                  class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
                >
                  <h1>
                    <Icon
                      icon="memory:eye-fill"
                      class="text-[1.3rem] md:text-[1.5rem]"
                    />
                  </h1>
                  <h1
                    class="underline underline-offset-2 text-[1rem] md:text-[1.2rem] text-gray-300 font-semibold font-mono"
                  >
                    tweet
                  </h1>
                </div>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- CSS -->
<style>
  /* Target the scrollbar for the desired element */
  .custom-scrollbar::-webkit-scrollbar {
    margin-top: 1rem;
    width: 2px;
    height: 0rem;
    background-color: black;
  }

  /* Style the scrollbar thumb */
  .custom-scrollbar::-webkit-scrollbar-thumb {
    background-color: #888;
    border-radius: 1px;
  }

  /* Style the scrollbar thumb when hovered */
  .custom-scrollbar::-webkit-scrollbar-thumb:hover {
    background-color: #555;
  }
  .slide-in {
    animation: slide-in 1.5s;
  }

  @keyframes slide-in {
    from {
      transform: translateX(100%);
    }
    to {
      transform: translateX(0);
    }
  }
  .slide-in2 {
    animation: slide-in 1.6s;
  }

  @keyframes slide-in2 {
    from {
      transform: translateX(100%);
    }
    to {
      transform: translateX(0);
    }
  }

  .slide-in3 {
    animation: slide-in 1.7s;
  }

  @keyframes slide-in3 {
    from {
      transform: translateX(100%);
    }
    to {
      transform: translateX(0);
    }
  }

  .flip-card {
    position: relative;
    width: 18rem;
    height: 19rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
    background: #1a2c50;
    border-radius: 1rem 0 1rem 0;
    background-image: url("../images/bg1.jpeg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    border-radius: 1rem 0 1rem 0;
  }

  @media (min-width: 768px) {
    .flip-card {
      width: auto;
      flex: 1 1 0%;
      min-width: 0;
      max-width: 22rem;
      height: 22rem;
    }
  }

  .hackathon-card {
    height: 18rem;
    padding-top: 1rem;
  }

  @media (min-width: 768px) {
    .hackathon-card {
      max-width: 25rem;
      height: 22rem;
      padding-top: 1.2rem;
    }
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
  .trophy-glow {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 0.4rem;
    border-radius: 50%;
    animation: trophy-pulse 3s ease-in-out infinite;
    transition:
      transform 0.3s ease,
      filter 0.3s ease;
  }

  .trophy-glow:hover {
    transform: scale(1.15);
    filter: drop-shadow(0 0 0.5rem rgba(251, 191, 36, 0.5));
  }

  @keyframes trophy-pulse {
    0%,
    100% {
      filter: drop-shadow(0 0 0.3rem rgba(251, 191, 36, 0.4));
    }
    50% {
      filter: drop-shadow(0 0 0.6rem rgba(251, 191, 36, 0.6));
    }
  }
  .hd-icon-hover {
    transition:
      transform 0.3s ease,
      filter 0.3s ease;
    cursor: pointer;
  }

  .hd-icon-hover:hover {
    transform: scale(1.2);
    filter: drop-shadow(0 0 0.4rem rgba(57, 167, 254, 0.6));
  }
</style>
