<script>
  import RegionsList from '../RegionsList.svelte';
  import RegionsSearch from '../RegionsSearch.svelte';
  import Navbar from '../Navbar.svelte'
  import Facts from '../Facts.svelte'
  import Footer from '../Footer.svelte'
</script>

<Navbar />
<main class="container container-small">
	<RegionsSearch />
  <Facts  />
</main>
<Footer />