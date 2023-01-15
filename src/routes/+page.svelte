<script>
  import RegionsList from '../RegionsList.svelte';
  import Navbar from '../Navbar.svelte'
  import Facts from '../Facts.svelte'
  import Footer from '../Footer.svelte'
</script>

<main class="container is-max-desktop content">
  <Navbar />

	<RegionsList />

  <div class="mt-5 mb-5">
    <Facts  />
  </div>
  
  <Footer />
</main>
