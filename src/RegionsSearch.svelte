<script>
	import { fade } from 'svelte/transition';
	import Geolocation from "svelte-geolocation";
	import GeoJsonGeometriesLookup from 'geojson-geometries-lookup';
	import 'bulma/css/bulma.css';
	import Button from 'svelma/src/components/Button.svelte';
	import CurrentLocationButton from './CurrentLocationButton.svelte';
	import regions from './regions.json';
	import Region from './Region.svelte';

	let searchterm;
	let position;

	const glookup = new GeoJsonGeometriesLookup(regions)

	function coordinateContainedInRegions(position) {
		console.log(position)
		const point1 = {type: "Point", coordinates: [position.coords.longitude, position.coords.latitude]};
		return glookup.getContainers(point1);
	}
</script>

<Geolocation getPosition bind:position />

{#if regions}
	<div class="field">
		<label class="label" for="searchterm">Suche:</label>
		<div class="control">
			<input class="input" type="text" bind:value={searchterm} placeholder="zB. Karlsplatz" />
			<Button on:click={() => (searchterm = undefined)}>Clear</Button>
		</div>
		<CurrentLocationButton />
	</div>

	{#if position != undefined && position.coords}
		{#each coordinateContainedInRegions(position).features as region}
			<Region {region} />
		{/each}
	{/if}

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
