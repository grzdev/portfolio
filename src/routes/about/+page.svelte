<!-- javascript -->
<script>
  // imports
  import About from "../../components/About.svelte";
  import LoadScreen from "../../components/LoadScreen.svelte";
  import Navbar from "../../components/Navbar.svelte";
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
    <Navbar {menuOpen} on:toggleMenu={() => (menuOpen = !menuOpen)} />
    <About />
  </div>
{/if}
