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
	{#if !coordinateContainedInRegions(position).features.empty}
		{#each coordinateContainedInRegions(position).features.sort(sortByArea) as region}
			<Region {region} />
		{/each}
	{:else}
		Unfortunately, we don't know any ticket apps of this region, yet.
		<br>
		If you know apps in your area, we are happy to 
		<a href="https://docs.google.com/forms/d/e/1FAIpQLSdHke4T1FK0I2_ICZaqHIskhmwuP17M7DEMAZqPlvX6AzhETg/viewform?usp=sf_link" target="_blank" rel="noreferrer">add new submissions</a>.
	{/if}
{:else}
	Unfortunately, we could not determine your position. Please allow access to your location in order to see available ticket append_styles.
{/if}
