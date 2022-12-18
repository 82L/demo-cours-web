<script lang="ts">
    export let imgData =null;
    const mapId = "2c9d64baf253f0ed"
    const apiKey = "AIzaSyDOpqarMHlQM79jhcMhE-s7CwM22f0XhR4"
    const zoom= 18
    console.log(imgData)

    function GetRotation(){
        return imgData.deviceDirection ? imgData.deviceDirection:0;
    }

</script>
{#if imgData != null}
    <img src="https://maps.googleapis.com/maps/api/staticmap?center={imgData.latitude},{imgData.longitude}&zoom={zoom}&size={window.screen.width}x{window.screen.width}&scale=2&format=jpg&map_id={mapId}&key={apiKey}"
    alt="Plan at coordinates ({imgData.latitude},{imgData.longitude}) taken on {imgData.dateKey}"
         style="transform: rotate({GetRotation()})"
         class="map-img"
    />

{/if}

<style>
    .map-img{
        border-radius: 50%;
        position: absolute;
        opacity: 0.5;
    }
</style>