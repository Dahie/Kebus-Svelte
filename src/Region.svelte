<script>
	import TransportApp from './TransportApp.svelte';

	export let region;
</script>


<p class="title mt-5 mb-3">{region.properties.title}</p>

{#each region.properties.apps as app}
	<TransportApp {app} />
{/each}
