
<!--App to show in a cumulative art form locations choosen and saved by the user-->

<script lang="ts">
  import SaveManager,  { LoadSavedData, data }  from "./lib/SaveManager.svelte";
  import CoordinateSavingButton from './lib/CoordinatesSavingButton.svelte';
  import ImgFetcher from "./lib/ImgFetcher.svelte";

  LoadSavedData()
  let mapsHidden = true
</script>

<main>
  <h1 class="title">Map Memories</h1>
  <div class="content">
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
  </div>

</main>

<style>

  .maps-container{
    position: relative;
    aspect-ratio: 1 / 1;
    background-color: #ffffff;
    border-radius: 50%;
    max-width: 90vmin;
    max-height: 90vmin;
    height: 100%;
    justify-content: center;
    align-items: center;
    display: flex;
  }
  .content{
    display: flex;
    flex-direction: column;
    /*justify-content: center;*/
    align-items: center;
    width: 100%;
    height: 100%;
    /*flex: 1;*/
    /*padding: 2rem;*/
    gap: 1rem;
  }
  main{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  .title{
    justify-self: flex-start;
    margin-bottom: 3rem;
  }
</style>