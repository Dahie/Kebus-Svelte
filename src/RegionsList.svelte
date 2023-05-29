<script>
	import { fade } from 'svelte/transition';
	import Geolocation from "svelte-geolocation";
	import GeoJsonGeometriesLookup from 'geojson-geometries-lookup';
	
	import CurrentLocationButton from './CurrentLocationButton.svelte';
	import regions from './regions.json';
	import Region from './Region.svelte';

	let position;

	const glookup = new GeoJsonGeometriesLookup(regions)

	function coordinateContainedInRegions(position) {
		const point1 = {type: "Point", coordinates: [position.coords.longitude, position.coords.latitude]};
		return glookup.getContainers(point1);
	}

	function sortByArea(a, b) {
		return a.properties.area - b.properties.area;
	}
</script>

<section>
	<Geolocation getPosition bind:position />

	<p>Around your current location the following Apps are available to purchase tickets for regional public transport.</p>
</section>

{#if position != undefined && position.coords}
	{#each coordinateContainedInRegions(position).features.sort(sortByArea) as region}
		<Region {region} />
	{/each}
{/if}
