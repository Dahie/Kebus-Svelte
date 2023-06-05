<script>
	import Map from '../../Map.svelte';
  import Navbar from '../../Navbar.svelte'
  import Footer from '../../Footer.svelte'
</script>

<svelte:head>
  <script defer async
  src="https://maps.googleapis.com/maps/api/js?key={import.meta.env.VITE_GOOGLE_MAPS_API_KEY}&callback=initMap">
  </script>
</svelte:head>


<Navbar />
<Map />
<Footer />
