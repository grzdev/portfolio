<!-- Javascript -->
<script lang="ts">
  import { onMount } from "svelte";
  import Avatar from "../images/3dPortraitt.png";
  import { fade } from "svelte/transition";
  import Icon from "@iconify/svelte";
  const options = ["javascript", "react", "typescript", "frontend"];
  let currentIndex = 0;
  let isPressed = false;  
  let isReleased = false;

  function handlePress() {
    isPressed = true;
    isReleased = false;
  }

  function handleRelease() {
    isPressed = false;
    isReleased = true;

    setTimeout(() => {
      isReleased = false;
    }, 200); // clear the animation class
  }


  // header text change
  function changeOption() {
    // header text change
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
  setInterval(changeOption, 5000);

  // imade fade in
  let fadeIn = false;
  onMount(() => {
    setTimeout(() => {
      fadeIn = true;
    }, 200);
  });

  // text fly in
  let showText1 = false;
  onMount(() => {
    setTimeout(() => {
      showText1 = true;
    }, 500);
  });
  let showText2 = false;
  onMount(() => {
    setTimeout(() => {
      showText2 = true;
    }, 900);
  });
  let showText3 = false;
  onMount(() => {
    setTimeout(() => {
      showText3 = true;
    }, 1300);
  });
  
</script>

<!-- HTML -->
<div
  class="flex flex-col-reverse sm:flex-col-reverse md:flex-row justify-center items-center text-white mt-[2rem] sm:mt-[1rem] md:mt-[3rem] gap-[2rem] sm:gap-[2rem] md:gap-[3rem] lg:gap-[6rem] md:mb-[2rem]"
>
  <!-- Name/Job -->
  <div class="w-[] sm:w-[35rem] md:w-[35rem]">
    <div
      class="flex flex-col justify-center sm:justify-center mt:justify-start items-center sm:items-center md:items-start"
    >
      {#if showText1}
        <h1
          class="text-gray-300 cursor-pointer font-mono hover:text-white transition duration-500 ease-in-out fly-in font-mono text-[1.8rem] mt-[-0.5rem] sm:mt-[-0.5rem] md:mt-[3rem] sm:text-[3rem] md:text-[3rem] font-bold"
        >
          hello, i'm dami
        </h1>
      {/if}
      {#if showText2}
        <h1
          class="text-gray-300 cursor-pointer font-mono hover:text-white transition duration-500 ease-in-out md:mt-[-0.1rem] fly-in font-mono text-[1.5rem] sm:text-[2rem] md:text-[2.5rem] font-bold"
        >
          a <span
            class="text-[#76c3ff] cursor-pointer font-mono hover:text-[#31a4fe] transition duration-500 ease-in-out"
            >software developer</span
          >
        </h1>
      {/if}
      {#if showText3}
        <div
          class="fly-in flex flex-row mt-[1.5rem] sm:mt-[1.5rem] md:mt-[2rem] gap-[2rem]"
        >
          <a href="/projects">
            <button>
              <span> Explore </span>
            </button>
          </a>
        </div>
      {/if}
    </div>
  </div>

  <!-- Avatar -->
  <div>
    {#if fadeIn}
      <div>
        <img
        src={Avatar}
        alt=""
        in:fade
        class="fade-transition w-[15rem] sm:w-[23rem] md:w-[25rem] cursor-pointer 
          {isPressed ? 'avatar-pressed' : ''} 
          {isReleased ? 'avatar-release' : ''}"
        on:mousedown={handlePress}
        on:mouseup={handleRelease}
        on:mouseleave={handleRelease}
        on:touchstart={handlePress}
        on:touchend={handleRelease}
      />
        <div class="move-container fade-transition" in:fade>
          <Icon
            
            icon="bxl:typescript"
            class="text-3xl sm:text-4xl md:text-5xl text-[#76c3ff] absolute mt-[-19rem] ml-[1rem] sm:mt-[-23rem] sm:ml-[4rem] md:mt-[-32rem] md:ml-[2rem] move"
          />
          <Icon
            icon="ri:javascript-fill"
            class="text-3xl sm:text-4xl md:text-5xl text-[#76c3ff]  absolute mt-[-17.5rem] ml-[12rem] sm:mt-[-20rem] sm:ml-[18rem] md:mt-[-29rem] md:ml-[20rem]"
          />
          <Icon
            icon="nonicons:svelte-16"
            class="text-3xl sm:text-4xl md:text-5xl text-[#76c3ff] absolute mt-[-10rem] ml-[-0.5rem] sm:mt-[-12rem] sm:ml-[1rem] md:mt-[-16rem] md:ml-[-1rem]"
          />
          <Icon
            icon="tabler:brand-react-native"
            class="text-3xl sm:text-4xl md:text-5xl text-[#76c3ff] absolute mt-[-9rem] ml-[13.5rem] sm:mt-[-10rem] sm:ml-[21rem] md:mt-[-14rem] md:ml-[22.5rem]"
          />
          <Icon
            icon="teenyicons:tailwind-solid"
            class="text-3xl sm:text-4xl md:text-5xl text-[#76c3ff] absolute mt-[-2rem] ml-[-2rem] sm:mt-[-3rem] sm:ml-[-1rem] md:mt-[-3rem] md:ml-[-3.5rem]"
          />
          <Icon
            icon="cib:blender"
            class="text-3xl sm:text-4xl md:text-5xl text-[#76c3ff]  absolute mt-[-1rem] ml-[14.5rem] sm:mt-[-2rem] sm:ml-[21rem] md:mt-[-2rem] md:ml-[24rem]"
          />
        </div>
      </div>
    {/if}
  </div>
</div>

<!-- CSS -->
<style>
  .move-container {
    animation: move 3s ease-in-out infinite;
  }

  @keyframes move {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-15px);
    }
  }

  .avatar-press {
  animation: press 0.4s ease;
}

@keyframes press {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(0.9); /* press in */
  }
  100% {
    transform: scale(1); /* bounce back */
  }
}
.avatar-pressed {
  transform: scale(0.9);
  transition: transform 0.1s ease;
}

.avatar-release {
  animation: popback 0.2s ease forwards;
}

@keyframes popback {
  0% {
    transform: scale(0.9);
  }
  100% {
    transform: scale(1);
  }
}


  button {
    padding: 0.1em 0.25em;
    width: 13em;
    height: 4.2em;
    background-color: #212121;
    border: 0.08em solid #fff;
    border-radius: 1rem 0 1rem 0;
    font-size: 12px;
  }

  button span {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: 700;
    bottom: 0.4em;
    width: 8.25em;
    height: 2.5em;
    background: rgb(12, 32, 56);
    background: linear-gradient(
      304deg,
      rgba(12, 32, 56, 1) 0%,
      rgba(57, 167, 254, 1) 100%
    );

    border-radius: 0.8rem 0 0.8rem 0;
    font-size: 1.5em;
    color: #fff;
    border: 0.08em solid #fff;
    box-shadow: 0 0.4em 0.1em 0.019em #d3d1d1;
  }

  button span:hover {
    transition: all 0.5s;
    transform: translate(0, 0.4em);
    box-shadow: 0 0 0 0 #d3d1d1;
  }

  button span:not(hover) {
    transition: all 1s;
  }
  .fly-in {
    animation: fly-in 1s ease-out, fade-in 1s ease-in;
  }

  @keyframes fly-in {
    from {
      transform: translateY(100%);
    }
    to {
      transform: translateY(0);
    }
  }

  @keyframes fade-in {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
</style>
