<div>
  <div class="flip-container mt-[1rem]">
    <div class="flip-card">
      <div
        class="flip-front bg-[#185a8e] rounded-tl-2xl rounded-br-2xl justify-center items-center flex flex-col"
      >
        <h1 class="text-3xl text-white font-mono font-bold">pennywise</h1>
        <p class="text-xl text-white font-mono font-bold mt-[1rem]">
          a daily expense tracker
        </p>
      </div>
      <div
        class="flip-back rounded-tl-2xl rounded-br-2xl justify-center items-center flex flex-col gap-[1rem]"
      >
        <div
          class="flex flex-row gap-[1rem] text-md sm:text-lg md:text-lg text-white font-semibold font-mono"
        >
          <h1>NEXTJS</h1>
          <h1>REACT</h1>
          <h1>CHAKRA-UI</h1>
        </div>
        <div
          class="flex flex-row gap-[1rem] text-md sm:text-lg md:text-lg text-white font-semibold font-mono"
        >
          <h1>LIVE LINK</h1>
          <h1>GITHUB REPO</h1>
        </div>
        <div
          class="flex flex-row gap-[1rem] text-md sm:text-lg md:text-lg text-white font-semibold font-mono text-center"
        >
          <h1>DATE STARTED: <br /> SEPT 2022</h1>
          <h1>DATE FINISHED: <br /> DEC 2022</h1>
        </div>
      </div>
    </div>
  </div>
</div>

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
      width: 18rem;
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
    background-color: #0b4473;
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
