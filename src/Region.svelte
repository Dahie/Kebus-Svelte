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
			{#if region.properties.notes}
				<p><em>{region.properties.notes}</em></p>
			{/if}
			{#each region.properties.apps as app}
				<TransportApp {app} />
			{/each}
		</div>
	</div>
</div>

<style>
	.panel {
		background-color: #EAC75C;
	}

	.panel .panel-head {
		background-color: #ECD56F;
	}
</style>
