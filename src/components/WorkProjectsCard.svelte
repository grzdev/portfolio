<script lang="ts">
  import Icon from "@iconify/svelte";
  import type { Project } from "./projectsInterface";
  export let projects2: Project[] = [];
</script>

{#each projects2 as project (project.id)}
  <div class="flip-container mt-[1rem]">
    <div class="flip-card">
      <div
        class="flip-front bg-[#00214e] rounded-tl-2xl rounded-br-2xl justify-center items-center flex flex-col"
      >
        <h1
          class="text-2xl sm:text-3xl md:text-3xl text-white font-mono font-bold"
        >
          {project.name}
        </h1>
        <p
          class="text-sm sm:text-xl md:text-xl text-white font-mono font-bold mt-[1rem] w-[14rem] text-center"
        >
          {project.desc}
        </p>
      </div>
      <div
        class="flip-back rounded-tl-2xl rounded-br-2xl justify-center items-center flex flex-col gap-[2rem]"
      >
        <div
          class="flex flex-row gap-[0.5rem] text-md sm:text-xl md:text-xl text-white font-semibold font-mono"
        >
          <h1>{project.tools.first}</h1>
          <h1>{project.tools.second}</h1>
          <h1>{project.tools.third}</h1>
        </div>
        <div
          class="flex flex-row gap-[1.7rem] text-md sm:text-xl md:text-xl text-white font-semibold font-mono"
        >
          <a href={project.link}>
            <div
              class="flex flex-row flex justify-center items-center gap-[0.7rem] font-semibold"
            >
              <h1><Icon icon="octicon:link-16" /></h1>
              <h1>link</h1>
            </div>
          </a>
          <a href={project.repo}>
            <div
              class="flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold"
            >
              <h1><Icon icon="octicon:repo-forked-16" /></h1>
              <h1>repo</h1>
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
    height: 12rem;
    border-radius: 1rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  @media (max-width: 640px) {
    /* Set different width and height for smaller screens */
    .flip-card {
      width: 17rem;
      height: 10rem;
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
    background-color: #000f24;
  }

  .container {
    display: flex;
  }

  .box {
    flex: 1;
    border: 1px solid #ccc;
    text-align: center;
    transition: transform 0.3s;
  }

  .flipped {
    transform: rotateY(180deg);
  }

  .button {
    margin-top: 20px;
  }
</style>
