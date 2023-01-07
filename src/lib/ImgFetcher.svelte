
<!--Charge an image base on the img data provided-->

<script lang="ts">
    export let imgData =null;
    const mapId = "2c9d64baf253f0ed";
    const apiKey = "AIzaSyCCkWjeIzdaqaCRU2XCown3TqsahvnbOS0";
    const zoom= 19;
    const scale = 1;

    function GetRotation(){
        return imgData.deviceDirection ? imgData.deviceDirection:0;
    }

</script>
{#if imgData != null}
    <img src="https://maps.googleapis.com/maps/api/staticmap?center={imgData.latitude},{imgData.longitude}&zoom={zoom}&size={window.screen.width}x{window.screen.width}&scale={scale}&format=jpg&map_id={mapId}&key={apiKey}"
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
        width: 100%;
        top:0;
        left: 0;
        height: 100%;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        /*color: #1a1a1a;*/
    }
</style>