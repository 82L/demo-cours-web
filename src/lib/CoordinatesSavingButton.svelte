
<!--Button to save coordinates of user device at instant of click-->

<script lang="ts">
  import SaveManager, { AddElementToData } from "./SaveManager.svelte";
  const locationOptions = {
    enableHighAccuracy: true
  }
  /**
   * Get current location and save position obtained If it does not work display alert.
   */
  const getLocationAndProcess = () => {
    if ('geolocation' in navigator) {
      navigator.geolocation.getCurrentPosition(AddElementToData, errorCallback, locationOptions);
    } else {
      alert("This device doesn't have geolocation")
    }

  }

  /**
   * Show an error in an alert message
   * @param error
   */
  const errorCallback = (error) => {
    alert(`ERROR(${error.code}): ${error.message}`);
  }
</script>

<button on:click={getLocationAndProcess}>
  Click to save location
</button>
