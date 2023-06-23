<script>
  import Navbar from '../../Navbar.svelte'
  import Footer from '../../Footer.svelte'
</script>

<svelte:head>
    <title>About - Kebus</title> 
		<meta name="description" content="How Kebus came to be, its purpose and how to contribute.">
</svelte:head>


<Navbar />
<main class="container">
	<section>
		<h1>About</h1>

		<p>
			You are travelling, you arrive in a new town. <br>
			So how do you get around? 
			Where do you find local buses?
			Where do you get tickets for regional public transport?
		</p>
		<p>
			While many transport companies have introduced digital services for ticket purchases, these are often fragmented and every organisation offers their own app.
			This is where Kebus helps. While it doesn't sell tickets, it helps you finding the available ticket apps in your area.
		</p>
		<p>
			Kebus is a work in progress. Germany alone has over 40 transport associations and to cover all will take time and help. 
			If you know missing apps in your area, we are happy to 
			<a href="https://docs.google.com/forms/d/e/1FAIpQLSdHke4T1FK0I2_ICZaqHIskhmwuP17M7DEMAZqPlvX6AzhETg/viewform?usp=sf_link" target="_blank" rel="noreferrer">add new submissions</a>.
		</p>
	</section>
</main>
<Footer />
