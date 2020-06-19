<script>
  import Welcome from "./screens/Welcomes.svelte";

  let state = "welcome"; // or "playing"
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 800px;
    margin: 0 auto;
    height: 100%;
    justify-content: center;
  }
</style>

<main>
  {#if state === 'welcome'}
    <Welcome />
  {:else if state === 'playing'}
    <p>Playing Screen goes here</p>
  {/if}
</main>
