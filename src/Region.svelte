<script>
	import TransportApp from './TransportApp.svelte';

	export let region;
</script>


<div class="panel">
	<div class="panel-head">
			<h2 class="panel-title">{region.properties.title}</h2>
	</div>

	<div class="panel-body">
		<div class="pricing-table row">
			{#each region.properties.apps as app}
				<TransportApp {app} />
			{/each}
		</div>
	</div>
</div>