<!-- Javascript -->
<script lang="ts">
</script>

<!-- HTML -->
<div class="flex justify-center items-center flex-col mt-[1rem]">
  <div class="flex justify-center items-center flex-col">
    <h1 class="text-white text-3xl font-mono font-bold">personal projects</h1>
    <div class="flip-container mt-[1rem]">
      <div class="flip-card">
        <div class="flip-front bg-[#093139] rounded-tl-2xl rounded-br-2xl" />
        <div class="flip-back rounded-tl-2xl rounded-br-2xl" />
      </div>
    </div>
  </div>
  <div class="flex justify-center items-center flex-col">
    <h1 class="text-white text-3xl font-mono font-bold mt-[1rem]">
      work related
    </h1>
    <div class="flip-container mt-[1rem]">
      <div class="flip-card">
        <div class="flip-front bg-[#093139] rounded-tl-2xl rounded-br-2xl" />
        <div class="flip-back rounded-tl-2xl rounded-br-2xl" />
      </div>
    </div>
  </div>
</div>

<!-- CSS -->
<style>
  .flip-container {
    perspective: 1000px;
  }

  .flip-card {
    width: 22rem;
    height: 15rem;
    border-radius: 1rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
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
    background-color: #208aa2;
  }
</style>
