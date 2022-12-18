
<!--App to show in a cumulative art form locations choosen and saved by the user-->

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
    aspect-ratio: 1/1;
    max-height: 100%;
    background-color: red;
  }
  main{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>