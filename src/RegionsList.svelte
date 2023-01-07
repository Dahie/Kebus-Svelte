<script>
	import { fade } from 'svelte/transition';
	//import 'bulma/css/bulma.css'
	//import { Button } from 'svelma';
	import regions from './regions.json';
	import Region from './Region.svelte';

	let searchterm;
</script>

{#if regions}
	<div class="field">
		<label class="label" for="searchterm">Suche:</label>
		<div class="control">
			<input class="input" type="text" bind:value={searchterm} placeholder="zB. Karlsplatz" />
			<!-- <Button on:click={() => (searchterm = undefined)}>Clear</Button> -->
		</div>
	</div>

	{#if searchterm != undefined}
		<table class="table is-fullwidth" transition:fade>
			<thead>
				<tr>
					<th>Title</th>
					<th>Apps</th>
				</tr>
			</thead>
			<tbody>
				{#each regions.features as region}
					{#if region.properties.title && region.properties.title.toLowerCase().startsWith(searchterm.toLowerCase())}
						<Region {region} />
					{/if}
				{/each}
			</tbody>
		</table>
	{/if}
{:else}
	<p class="loading">loading...</p>
{/if}

<style>
	.input {
		width: 70%;
	}
</style>
