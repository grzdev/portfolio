<!-- Javascript -->
<script lang="ts">
  import ProjectsCard from "../components/ProjectsCard.svelte";
  import type { Project, Project2 } from "../components/projectsInterface";
  import personalProjects from "../components/personalProjects.json";
  import workProjects from "../components/workProjects.json";
  import WorkProjectsCard from "../components/WorkProjectsCard.svelte";
  export let projects: Project[] = personalProjects.personal;
  export let projects2: Project2[] = workProjects.work;

  import { onMount } from "svelte";
  import { fade } from "svelte/transition";

  let showDiv = false;

  onMount(() => {
    showDiv = true;
  });
</script>

<!-- HTML -->
<div
  class="flex flex-col px-[1rem] sm:px-[2rem] md:px-[4rem] mt-[1rem] sm:mt-[1rem] md:mt-[1rem] overflow-x-hidden"
>
  <div class="flex flex-col">
    <h1
      class="text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out text-xl sm:text-3xl md:text-3xl font-mono font-bold"
      in:fade
    >
      featured
    </h1>
    <div
      class="flex flex-row mt-[0.3rem] gap-[1.3rem] sm:gap-[2rem] md:gap-[2rem] overflow-x-auto custom-scrollbar"
      class:slide-in={showDiv}
    >
      <ProjectsCard {projects} />
    </div>
  </div>
  <div class="flex flex-col mt-[1rem] sm:mt-[2rem] md:mt-[2rem]">
    <h1
      class="text-gray-300 font-mono hover:text-white transition duration-500 ease-in-out text-xl sm:text-3xl md:text-3xl font-mono font-bold mt-[1rem]"
      in:fade
    >
      others
    </h1>
    <div
      class="flex flex-row mt-[0.3rem] gap-[1.3rem] sm:gap-[2rem] md:gap-[2rem] overflow-x-auto custom-scrollbar"
      class:slide-in2={showDiv}
    >
      <WorkProjectsCard {projects2} />
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
</style>
