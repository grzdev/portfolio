<script lang="ts">
  import Icon from "@iconify/svelte";
  import type { Project } from "./projectsInterface";
  export let projects: Project[] = [];

  let flippedCardId: number | null = null;

  const toggleFlip = (id: number) => {
    flippedCardId = flippedCardId === id ? null : id;
  };
</script>

<!-- personal projects -->
{#each projects as project (project.id)}
  <div
    class="flip-container move-container mt-[1rem]"
    on:click={() => toggleFlip(project.id)}
    on:keydown={(e) => e.key === "Enter" && toggleFlip(project.id)}
    role="button"
    tabindex="0"
    aria-label="Project card flip"
  >
    <div class="flip-card" class:flipped={flippedCardId === project.id}>
      <div class="flip-front justify-center items-center flex flex-col">
        <h1 class="text-gray-200 text-2xl sm:text-3xl md:text-3xl font-mono font-bold">
          {project.name}
        </h1>
        <p class="text-gray-200 text-sm sm:text-xl md:text-xl font-mono font-bold mt-[1rem] w-[14rem] sm:w-[16rem] md:w-[16rem] text-center">
          {project.desc}
        </p>
        <p class="text-gray-200 text-[0.7rem] sm:text-[0.9rem] md:text-[1rem] font-mono font-bold mt-[2.5rem] w-[14rem] text-center">
          {project.type}
        </p>
      </div>
      <div class="flip-back justify-center items-center flex flex-col gap-[2rem]">
        <div class="text-gray-300 flex flex-row gap-[0.8rem] md:gap-[0.5rem] text-[0.8rem] sm:text-xl md:text-xl font-semibold font-mono">
          <h1>{project.tools.first}</h1>
          <h1>{project.tools.second}</h1>
          <h1>{project.tools.third}</h1>
        </div>
        <div class="flex flex-row gap-[1.9rem] text-[0.9rem] sm:text-xl md:text-xl font-semibold font-mono">
          <a href={project.link} target="_blank" rel="noopener noreferrer">
            <div class="flex flex-row justify-center items-center gap-[0.4rem] font-semibold text-gray-300">
              <h1><Icon icon="octicon:link-16" /></h1>
              <h1 class="underline underline-offset-2">link</h1>
            </div>
          </a>
          <a href={project.repo} target="_blank" rel="noopener noreferrer">
            <div class="text-gray-300 flex flex-row justify-center items-center gap-[0.2rem] font-semibold">
              <h1><Icon icon="octicon:repo-forked-16" /></h1>
              <h1 class="underline underline-offset-2">repo</h1>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
{/each}

<style>
  .flip-card {
    position: relative;
    width: 22rem;
    height: 13rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  .flip-card.flipped {
    transform: rotateY(180deg);
  }

  @media (max-width: 640px) {
    .flip-card {
      width: 18rem;
      height: 12rem;
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
    background-image: url("../images/bg1.jpeg");
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
