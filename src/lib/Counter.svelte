<script lang="ts">
  const locationOptions = {
    enableHighAccuracy: true
  }
  let count: number = 0
  const getLocationAndProcess = () => {
    if ('geolocation' in navigator) {
      navigator.geolocation.getCurrentPosition(useLocation, errorCallback, locationOptions);
    } else {
      alert("This device doesn't have geolocation")
    }

  }

  const useLocation = (position) => {
      let latitude = position.coords.latitude;
      let longitude = position.coords.longitude;
      let deviceDirection = position.coords.heading;
      const url = `https://maps.googleapis.com/maps/api/staticmap?
      center=${latitude},${longitude}
      &zoom=20
      &size=${window.screen.width}x${window.screen.width}
      &scale=2
      &format=jpg
      &map_id=2c9d64baf253f0ed
      &key=AIzaSyDOpqarMHlQM79jhcMhE-s7CwM22f0XhR4`;

      fetch(url)
              .then(response => response.blob())
              .then(imageBlob => {
                
              })
  }
  const errorCallback = (error) => {
    alert(`ERROR(${error.code}): ${error.message}`);
  }
</script>

<button on:click={getLocationAndProcess}>
  Click to save location
</button>
