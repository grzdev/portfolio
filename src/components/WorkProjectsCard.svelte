<script lang="ts">
  import Icon from "@iconify/svelte";
  import type { Project } from "./projectsInterface";
  export let projects2: Project[] = [];
</script>

{#each projects2 as project (project.id)}
  <div class="flip-container move-container mt-[1rem]">
    <div class="flip-card">
      <div
        class="flip-front bg-[#142A66] rounded-tl-2xl rounded-br-2xl justify-center items-center flex flex-col"
      >
        <h1
          class="text-2xl sm:text-3xl md:text-3xl text-gray-200 font-mono font-bold"
        >
          {project.name}
        </h1>
        <p
          class="text-sm sm:text-xl md:text-xl text-gray-200 font-mono font-bold mt-[1rem] w-[14rem] text-center"
        >
          {project.desc}
        </p>
        <p
          class="text-gray-200 text-[0.5rem] sm:text-[0.8rem] md:text-[0.9rem] font-mono font-bold mt-[2.5rem] w-[14rem] text-center"
        >
          {project.type}
        </p>
      </div>
      <div
        class="flip-back rounded-tl-2xl rounded-br-2xl justify-center items-center flex flex-col gap-[2rem]"
      >
        <div
          class="flex flex-row gap-[0.5rem] text-[0.8rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono"
        >
          <h1>{project.tools.first}</h1>
          <h1>{project.tools.second}</h1>
          <h1>{project.tools.third}</h1>
        </div>
        <div
          class="flex flex-row gap-[1.9rem] text-[0.9rem] sm:text-xl md:text-xl font-semibold font-mono"
        >
          <a href={project.link}>
            <div
              class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
            >
              <h1><Icon icon="octicon:link-16" /></h1>
              <h1 class="underline underline-offset-2">link</h1>
            </div>
          </a>
          <a href={project.repo}>
            <div
              class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.2rem] font-semibold"
            >
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
    width: 22rem;
    height: 13rem;
    border-radius: 1rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  @media (max-width: 640px) {
    /* Set different width and height for smaller screens */
    .flip-card {
      width: 17rem;
      height: 11rem;
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

  .flip-back {
    transform: rotateY(180deg);
    background-color: #051133;
  }
  .move-container {
    animation: move 2s ease-in-out infinite;
  }

  @keyframes move {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-8px);
    }
  }
</style>
