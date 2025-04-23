<!-- Javascript -->
<script lang="ts">
  import ProjectsCard from "../components/ProjectsCard.svelte";
  import type { Project, Project2 } from "../components/projectsInterface";
  import personalProjects from "../components/personalProjects.json";
  export let projects: Project[] = personalProjects.personal;
  import Donut from "../images/content.jpg"
  import Pennywise from "../images/pennywise4.png"
  import yezir from "../images/yezir3.png"
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";
  import Icon from "@iconify/svelte";

  let showDiv = false;

  onMount(() => {
    showDiv = true;
  });
</script>

<!-- HTML -->
<div
  class="flex flex-col px-[1rem] sm:px-[2rem] md:px-[4rem] mt-[1rem] sm:mt-[1rem] md:mt-[2rem] overflow-x-hidden md:mb-[1rem]"
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
  <div class="flex flex-col mt-[1rem] sm:mt-[2rem] md:mt-[1rem] mb-[2rem]">
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
      <!-- others/> -->
       <div class=" move-container mt-[1rem] flex flex-row gap-[2rem]">
        
        <!-- donut -->
         <div class="flip-card justify-center items-center flex flex-col ">
          <div class="relative">
            <img
              src={Donut}
              alt=""
              class="w-[14rem] md:w-[16rem] rounded-[1rem]"
            />
            <Icon icon="logos:blender" class="absolute top-2 left-2 text-[1.1rem] md:text-[1.5rem]" />
            <Icon 
              icon="skill-icons:instagram" 
              class="absolute top-2 right-2 text-[1.1rem] md:text-[1.5rem]" 
            />
            </div>
             <div class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem]">
              <h1 class="text-[1.2rem] md:text-[1.5rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono">
               3d donut
              </h1>
              <a href="https://www.instagram.com/share/BAMGK-fYZ9" target="_blank" rel="noopener noreferrer" >
                <div class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold">
                  <h1><Icon icon="octicon:link-16" /></h1>
                  <h1 class="underline underline-offset-2">link</h1>
                </div>
              </a>
           </div>
         </div>

           <!-- pennywise -->
           <div class="flip-card justify-center items-center flex flex-col ">
            <div class="relative">
              <img
                src={Pennywise}
                alt=""
                class="w-[14.5rem] md:w-[17.5rem]  rounded-[1rem]"
              />
              <Icon 
                icon="skill-icons:linkedin"
                class="absolute top-2 right-2 text-[1.1rem] md:text-[1.5rem]" 
              />
            </div>
              <div class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem]">
                <h1 class="text-[1.2rem] md:text-[1.5rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono">
                 pennywise
                </h1>
                <a href="https://www.linkedin.com/posts/dami-oyeniyi-97805b23a_fintech-personalproject-react-ugcPost-7076183377304838144-b-pP?utm_medium=ios_app&rcm=ACoAADtzxKwBnNXukmm6xAG7XUw5ax_VVEvNlbk&utm_source=social_share_send&utm_campaign=copy_link " target="_blank" rel="noopener noreferrer" >
                  <div class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold">
                    <h1><Icon icon="octicon:link-16" /></h1>
                    <h1 class="underline underline-offset-2">link</h1>
                  </div>
                </a>
             </div>
           </div>

            <!-- yezir -->
            <div class="flip-card justify-center items-center flex flex-col ">
              <div class="relative">
                <img
                  src={yezir}
                  alt=""
                  class="w-[14.5rem] md:w-[17.5rem]  rounded-[1rem]"
                />
                <Icon 
                  icon="skill-icons:instagram" 
                  class="absolute top-2 right-2 text-[1.1rem] md:text-[1.5rem]" 
                />
              </div>
                 <div class="flex flex-col justify-center items-center mt-[1rem] gap-[0.2rem]">
                  <h1 class="text-[1.2rem] md:text-[1.5rem] sm:text-xl md:text-xl text-gray-300 font-semibold font-mono">
                   yezir hasan
                  </h1>
                  <a href="https://yezirhasan.netlify.app/" target="_blank" rel="noopener noreferrer" >
                    <div class="text-gray-300 flex flex-row flex justify-center items-center gap-[0.4rem] font-semibold">
                      <h1><Icon icon="octicon:link-16" /></h1>
                      <h1 class="underline underline-offset-2">link</h1>
                    </div>
                  </a>
               </div>
             </div>

       </div>
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

  .flip-card {
    position: relative;
    width: 22rem;
    height: 20rem;
    transition: transform 0.5s;
    transform-style: preserve-3d;
    background: #1A2C50;
    border-radius: 1rem 0 1rem 0;
    background-image: url("../images/bg1.jpeg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    border-radius: 1rem 0 1rem 0;
  }


  @media (max-width: 640px) {
    .flip-card {
      width: 18rem;
      height: 16rem;
    }
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
