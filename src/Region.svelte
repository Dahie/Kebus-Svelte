<script>
	import TransportApp from './TransportApp.svelte';

	export let region;
</script>


<div class="panel">
	<div class="panel-head">
		<h2 class="panel-title">{region.properties.title}</h2>
	</div>

	<div class="panel-body">
		<ul class="tags">
			{#each region.properties.location_tags.split(/\,/) as tag}
				<li class="tag tag-rounded">{tag}</li>
			{/each}
		</ul>
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
	.tags .tag {
		box-shadow: none;
		font-size: 0.7rem;
		margin-bottom: 0.4rem;
	}

	.panel {
		background-color: #EAC75C;
	}

	.panel .panel-head {
		background-color: #ECD56F;
	}
</style>
