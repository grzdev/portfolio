<script lang="ts">
  import Avatar from "../images/avatar.png";
  const options = ["Javascript", "React", "Typescript"];
  let currentIndex = 0;

  function changeOption() {
    const optionsElement = document.getElementById("options");
    if (optionsElement) {
      optionsElement.classList.add("fade-out");

      setTimeout(() => {
        optionsElement.textContent = options[currentIndex];
        optionsElement.classList.remove("fade-out");
      }, 500);

      currentIndex++;
      if (currentIndex >= options.length) {
        currentIndex = 0;
      }
    }
  }

  setInterval(changeOption, 6000);
</script>

<div
  class="flex flex-col-reverse sm:flex-col-reverse md:flex-row justify-center items-center text-white mt-[2rem] sm:mt-[1rem] md:mt-[4rem] gap-[2rem] sm:gap-[2rem] md:gap-[4rem]"
>
  <div class="w-[] sm:w-[35rem] md:w-[35rem]">
    <div
      class="flex flex-col justify-center sm:justify-center mt:justify-start items-center sm:items-center md:items-start"
    >
      <h1
        class="text-[2.4rem] mt-[-1rem] sm:mt-[-2rem] md:mt-[2rem] sm:text-[3rem] md:text-[4rem] font-bold"
      >
        Hey, I'm Damilola
      </h1>
      <h1 class="text-[1.5rem] sm:text-[2rem] md:text-[2.5rem] font-bold">
        A <span id="options">Frontend</span> developer
      </h1>
      <div class="flex flex-row mt-[2rem] sm:mt-[2rem] md:mt-[2rem] gap-[2rem]">
        <button>
          <span> Explore</span>
        </button>
      </div>
    </div>
  </div>
  <div>
    <img class="w-[20rem] sm:w-[23rem] md:w-[30rem]" src={Avatar} alt="" />
  </div>
</div>

<style>
  /* @keyframes fly {
    0% {
      transform: translateY(-100%);
    }
    100% {
      transform: translateY(0);
    }
  }

  .fly-animation {
    animation: fly 1s ease-in-out;
  } */
  button {
    padding: 0.1em 0.25em;
    width: 13em;
    height: 4.2em;
    background-color: #212121;
    border: 0.08em solid #fff;
    border-radius: 0.3em;
    font-size: 12px;
  }

  button span {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    bottom: 0.4em;
    width: 8.25em;
    height: 2.5em;
    background-color: #212121;
    border-radius: 0.2em;
    font-size: 1.5em;
    color: #fff;
    border: 0.08em solid #fff;
    box-shadow: 0 0.4em 0.1em 0.019em #fff;
  }

  button span:hover {
    transition: all 0.5s;
    transform: translate(0, 0.4em);
    box-shadow: 0 0 0 0 #fff;
  }

  button span:not(hover) {
    transition: all 1s;
  }
</style>
