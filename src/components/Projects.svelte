<!-- Javascript -->
<script lang="ts">
  import ProjectsCard from "./ProjectsCard.svelte";
</script>

<!-- HTML -->
<div class="flex flex-col px-[1rem] sm:px-[4rem] md:px-[4rem] mt-[1rem]">
  <div class="flex flex-col">
    <h1 class="text-gray-200 text-3xl font-mono font-bold">
      personal projects
    </h1>
    <ProjectsCard />
  </div>
  <div class="flex flex-col mt-[2rem]">
    <h1 class="text-gray-200 text-3xl font-mono font-bold mt-[1rem]">
      work related
    </h1>
    <ProjectsCard />
  </div>
</div>

<!-- CSS -->
<style>
</style>
