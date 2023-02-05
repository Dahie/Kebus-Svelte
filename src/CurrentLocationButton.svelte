<script>
  function panToCurrentLocation() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(
        (position) => {
          const pos = {
            lat: position.coords.latitude,
            lng: position.coords.longitude,
          };
          console.log(pos)
        },
        () => {
          
        }
      );
    } else {
      // Browser doesn't support Geolocation
    }
  }

</script>

<button class="custom-map-control-button block" on:click={panToCurrentLocation}>Current Location</button>