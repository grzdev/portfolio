<script lang="ts">
  import Icon from "@iconify/svelte";
  import type { Project } from "./projectsInterface";
  export let projects: Project[] = [];

  let flippedCardId: number | null = null;
  let hasFlipped = false;

  const toggleFlip = (id: number) => {
    flippedCardId = flippedCardId === id ? null : id;
    hasFlipped = true;
  };
</script>

<!-- personal projects -->
{#each projects as project (project.id)}
  <div
    class="flip-container move-container mt-[1rem] md:flex-1 md:min-w-0"
    on:click={() => toggleFlip(project.id)}
    on:keydown={(e) => e.key === "Enter" && toggleFlip(project.id)}
    role="button"
    tabindex="0"
    aria-label="Project card flip"
  >
    {#if project.id === 1 && !hasFlipped}
      <div class="tap-hint">
        <Icon icon="fluent:tap-single-48-filled" class="text-[2rem] text-white drop-shadow-lg" />
      </div>
    {/if}
    <div class="flip-card" class:flipped={flippedCardId === project.id}>
      <!-- front -->
      <div class="flip-front flex flex-col items-center pt-[0.8rem]">
        {#if project.image}
          <img
            src={project.image}
            alt={project.name}
            loading="lazy"
            class="w-[15rem] md:w-[17rem] h-[10rem] object-cover rounded-[1rem]"
          />
        {/if}
        <div class="flex flex-col items-center mt-[0.7rem] gap-[0.25rem]">
          <h1
            class="text-gray-200 text-[1.2rem] md:text-[1.5rem] font-mono font-bold"
          >
            {project.name}
          </h1>
          <p
            class="text-gray-200 text-[0.7rem] md:text-[0.9rem] font-mono font-bold underline underline-offset-2"
          >
            {project.type}
          </p>
        </div>
      </div>
      <!-- back -->
      <div
        class="flip-back justify-center items-center flex flex-col gap-[2rem]"
      >
        <p
          class="text-gray-300 text-[0.8rem] sm:text-[0.9rem] md:text-[1.1rem] font-semibold font-mono text-center"
        >
          {project.desc}
        </p>
        <div
          class="text-gray-300 flex flex-row flex-wrap justify-center gap-[0.8rem] md:gap-[0.5rem] text-[0.8rem] sm:text-[0.9rem] md:text-[1.1rem] font-semibold font-mono"
        >
          {#if project.tools.first}<h1>{project.tools.first}</h1>{/if}
          {#if project.tools.second}<h1>{project.tools.second}</h1>{/if}
          {#if project.tools.third}<h1>{project.tools.third}</h1>{/if}
        </div>
        <div
          class="flex flex-row gap-[1.9rem] text-[0.9rem] sm:text-[1rem] md:text-[1.1rem] font-semibold font-mono"
        >
          <a
            href={project.link}
            target="_blank"
            rel="noopener noreferrer"
            on:click|stopPropagation
          >
            <div
              class="flex flex-row justify-center items-center gap-[0.4rem] font-semibold text-gray-300"
            >
              <Icon icon="octicon:link-16" />
              <span class="underline underline-offset-2">link</span>
            </div>
          </a>
          <a
            href={project.repo}
            target="_blank"
            rel="noopener noreferrer"
            on:click|stopPropagation
          >
            <div
              class="text-gray-300 flex flex-row justify-center items-center gap-[0.2rem] font-semibold"
            >
              <Icon icon="octicon:repo-forked-16" />
              <span class="underline underline-offset-2">repo</span>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
{/each}

<style>
  .flip-container {
    position: relative;
  }

  .flip-card {
    position: relative;
    width: 18rem;
    height: 18rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  .flip-card.flipped {
    transform: rotateY(180deg);
  }

  @media (min-width: 768px) {
    .flip-card {
      width: 100%;
      height: 19rem;
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

  .tap-hint {
    position: absolute;
    bottom: -1rem;
    right: -0.8rem;
    z-index: 10;
    animation: tap-pulse 2s ease-in-out infinite;
    pointer-events: none;
    user-select: none;
  }

  @keyframes tap-pulse {
    0%, 100% { transform: scale(1); opacity: 0.8; }
    50% { transform: scale(1.3); opacity: 1; }
  }

  .flip-back {
    transform: rotateY(180deg);
    background-color: #1a2c50;
    border-radius: 1rem 0 1rem 0;
    padding: 1.5rem;
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
