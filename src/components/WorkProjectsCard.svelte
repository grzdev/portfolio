<script lang="ts">
  import Icon from "@iconify/svelte";
  import type { Project2 } from "./projectsInterface";
  export let projects2: Project2[] = [];

  let flippedCardId: number | null = null;

  const toggleFlip = (id: number) => {
    flippedCardId = flippedCardId === id ? null : id;
  };
</script>

<!-- work projects -->
{#each projects2 as project (project.id)}
  <div
    class="flip-container move-container mt-[1rem]"
    on:click={() => toggleFlip(project.id)}
    on:keydown={(e) => e.key === "Enter" && toggleFlip(project.id)}
    role="button"
    tabindex="0"
    aria-label="Work project card flip"
  >
    <div class="flip-card" class:flipped={flippedCardId === project.id}>

      <!-- front page -->
      <div class="flip-front justify-center items-center flex flex-col">
        
      </div>

      <!-- back oage -->
      <div class="flip-back justify-center items-center flex flex-col gap-[2rem]">
        <div class="flex flex-row gap-[0.5rem] text-[0.8rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono">
          <h1>{project.tools.first}</h1>
          <h1>{project.tools.second}</h1>
          <h1>{project.tools.third}</h1>
        </div>
        <div class="flex flex-row gap-[1.9rem] text-[0.9rem] sm:text-xl md:text-xl font-semibold font-mono">
          <a href={project.link} target="_blank" rel="noopener noreferrer" >
            <div class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold">
              <h1><Icon icon="octicon:link-16" /></h1>
              <h1 class="underline underline-offset-2">link</h1>
            </div>
          </a>
          <a href={project.repo} target="_blank" rel="noopener noreferrer">
            <div class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.2rem] font-semibold">
              <h1><Icon icon="octicon:repo-forked-16" /></h1>
              <h1 class="underline underline-offset-2">repo</h1>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
{/each}

<!-- CSS -->
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
      width: 17rem;
      height: 11rem;
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
    /* background-image: url("../images/bg1.jpeg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    border-radius: 1rem 0 1rem 0; */
    background: #1A2C50;
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
