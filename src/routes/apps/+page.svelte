<script>
	import AppsList from './AppsList.svelte';
  import Navbar from '../../Navbar.svelte'
  import Footer from '../../Footer.svelte'
</script>

<svelte:head>
    <title>Apps - Kebus</title> 
    <meta name="description" content="Kebus provides an index of Ticket Apps for regional and city public transport in its respective areas.">
</svelte:head>

<Navbar />
<main class="container">
	<AppsList />  
</main>
<Footer />
