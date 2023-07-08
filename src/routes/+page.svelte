<!-- javascript -->
<script>
  // imports
  import Navbar from "../modules/Navbar.svelte";
  import Home from "../modules/Home.svelte";
  import LoadScreen from "../components/LoadScreen.svelte";
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
    <Home />
  </div>
{/if}

<!-- css -->
<style lang="postcss">
  :global(html) {
    background-color: black;
  }
</style>
