<script>
	import { fade } from 'svelte/transition';
	import Geolocation from "svelte-geolocation";
	import GeoJsonGeometriesLookup from 'geojson-geometries-lookup';
	import CurrentLocationButton from './CurrentLocationButton.svelte';
	import regions from './regions.json';
	import Region from './Region.svelte';

	let searchterm;
	let position;

	const glookup = new GeoJsonGeometriesLookup(regions)

	function coordinateContainedInRegions(position) {
		const point1 = {type: "Point", coordinates: [position.coords.longitude, position.coords.latitude]};
		return glookup.getContainers(point1);
	}
</script>

<section>
	<Geolocation getPosition bind:position />
	<p>Find apps to purchase tickets for regional and city buses in your area.</p>
	<div class="form-control search-control">
		<input class="input" type="text" bind:value={searchterm} placeholder="Show at current location" />
		<button on:click={() => (searchterm = undefined)}>❌</button>
	</div>
</section>

{#if regions}
	{#if searchterm != undefined || searchterm == ""}
		{#each regions.features as region}
			{#if (region.properties.title && region.properties.title.toLowerCase().startsWith(searchterm.toLowerCase()) || (region.properties.location_tags && region.properties.location_tags.toLowerCase().includes(searchterm.toLowerCase())))}
				<Region {region} />
			{/if}
		{/each}
	{:else}
		{#if position != undefined && position.coords}
			{#each coordinateContainedInRegions(position).features as region}
				<Region {region} />
			{/each}
		{/if}
	{/if}
{:else}
	<p class="loading">loading...</p>
{/if}

<style>
	.input {
		display: inline;
		width: 70%;
	}
</style>
