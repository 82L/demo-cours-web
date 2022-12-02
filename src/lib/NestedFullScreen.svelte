<script lang="ts">

    function toggleFullScreen1(){
        let element = document.getElementById("first-level")
        if(document.fullscreenElement != element)
        {
            element.requestFullscreen();
        }
        else {
            document.exitFullscreen();
        }

    }
    function toggleFullScreen2(){
        let element = document.getElementById("second-level")
        if(document.fullscreenElement != element)
        {
            element.requestFullscreen();
        }
        else {
            document.exitFullscreen();
        }

    }

</script>
<div id="first-level" class="cube">
    <div class="content">
        <div id="second-level" class="cube" >
            <div class="content">
                <button class="close-fullscreen" on:click={toggleFullScreen2}>toggle Fullscreen2</button>
            </div>
        </div>
        <button class="close-fullscreen" on:click={toggleFullScreen1}>toggle Fullscreen1</button>
        <button class="close-fullscreen"  on:click={toggleFullScreen2}>toggle Fullscreen2</button>
    </div>
</div>
<button class="close-fullscreen" on:click={toggleFullScreen1}>toggle Fullscreen1</button>
<style>
    #first-level{
        background-color: rgba(0,255,0,0.2);
    }
    #second-level{
        background-color: rgba(0,0,255,0.2);
    }
    .cube::backdrop{
        background-color: transparent;
    }
    .cube > .content{
        opacity: 0;
        visibility: hidden;
    }
    .cube:fullscreen > .content{
        opacity: 1;
        visibility: visible;
    }
    .cube{
        width: 20px;
        height: 20px;
        overflow: hidden;
    }
</style>