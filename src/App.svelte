<script lang="ts">
  import SaveManager,  { LoadSavedData, data }  from "./lib/SaveManager.svelte";
  import CoordinateSavingButton from './lib/CoordinatesSavingButton.svelte';
  import ImgFetcher from "./lib/ImgFetcher.svelte";

  LoadSavedData()
  let mapsHidden = true
</script>

<main>
  <button on:click={e => mapsHidden= !mapsHidden}>Toggle Maps</button>
  {#if mapsHidden}
    <CoordinateSavingButton/>
  {:else }
    <div class="maps-container">
    {#each data as element}
      <ImgFetcher imgData={element} />
    {/each}
    </div>
  {/if}

</main>

<style>
  .maps-container{
    position: relative;
  }
</style>