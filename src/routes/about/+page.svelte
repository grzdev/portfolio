<!-- javascript -->
<script>
  // imports
  import About from "../../modules/About.svelte";
  import LoadScreen from "../../components/LoadScreen.svelte";
  import Navbar from "../../modules/Navbar.svelte";
  let menuOpen = false;

  // LoadScreen
  let isLoading = true;
  setTimeout(() => {
    isLoading = false;
  }, 2000);
</script>

<!-- html -->
{#if isLoading}
  <LoadScreen />
{:else}
  <div>
    <title>Dami Oyeniyi | About</title>
    <Navbar {menuOpen} on:toggleMenu={() => (menuOpen = !menuOpen)} />
    <About />
  </div>
{/if}
