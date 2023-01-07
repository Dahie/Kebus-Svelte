<script>
	import TransportApp from './TransportApp.svelte';

	export let region;
</script>

<tr>
	<td>{region.properties.title}</td>
	<td>
		{#each region.properties.apps as app}
			<TransportApp {app} />
		{/each}
	</td>
</tr>
