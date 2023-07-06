<!-- Javascript -->
<script lang="ts">
</script>

<!-- HTML -->
<div class="flex justify-center items-center">
  <!-- <h1 class="text-white">projects</h1> -->
  <div class="flip-container">
    <div class="flip-card">
      <div
        class="flip-front bg-[#25AFCE] w-[25rem] h-[20rem] rounded-tl-2xl rounded-br-2xl"
      />
      <div
        class="flip-back bg-[#0f4652] w-[25rem] h-[20rem] rounded-tl-2xl rounded-br-2xl"
      />
    </div>
  </div>
</div>

<!-- CSS -->
<style>
  .flip-container {
    perspective: 1000px;
  }

  .flip-card {
    width: 25rem;
    height: 20rem;
    border-radius: 1rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
  }

  .flip-container:hover .flip-card {
    transform: rotateY(180deg);
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
    background-color: #0f4652;
  }
</style>
