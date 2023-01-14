<script>
	import TransportApp from './TransportApp.svelte';

	export let region;
</script>


<h2>{region.properties.title}</h2>
{#each region.properties.apps as app}
	<TransportApp {app} />
{/each}
