<!-- javascript -->
<!-- imports -->
<script>
  import LoadScreen from "../components/LoadScreen.svelte";
  import Navbar from "../components/Navbar.svelte";
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
  </div>
{/if}

<!-- css -->
<style lang="postcss">
  :global(html) {
    background-color: black;
  }
</style>
