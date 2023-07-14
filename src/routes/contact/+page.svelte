<!-- javascript -->
<script>
  // imports
  import LoadScreen from "../../components/LoadScreen.svelte";
  import Contact from "../../modules/Contact.svelte";
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
    <Navbar {menuOpen} on:toggleMenu={() => (menuOpen = !menuOpen)} />
    <Contact />
  </div>
{/if}

<style lang="postcss">
  :global(html) {
    background-color: black;
  }
</style>
