<script>
	import geojson from './regions.json';
  import { onMount } from 'svelte';
  import { locations, map } from './stores.js';

  //let infoWindow = new google.maps.InfoWindow();

  let mapId = "map-container";

  function importGeoJson(data) {
    const locationsNew = [];
    for(const entry of data.features) {
      if(entry.geometry.type == 'Point') {
        locationsNew.push(createPointFeature(entry));
      }
      else if (entry.geometry.type == 'LineString') {
        locationsNew.push(createLineStringFeature(entry, entry.geometry.coordinates));
      } else if (entry.geometry.type == 'MultiLineString') {
        for(const route of entry.geometry.coordinates) {
          locationsNew.push(createLineStringFeature(entry, route));
        }
      } else if (entry.geometry.type == 'Polygon') {
        for(const route of entry.geometry.coordinates) {
          locationsNew.push(createPolygonStringFeature(entry, route));
        }
      }
    }
    console.log(locationsNew)
    locations.set($locations.concat(locationsNew));
  }

  function mapRouteCoordinates(coordinates) {
    const routeCoordinates = [];

    for(const coordinate of coordinates) {
      routeCoordinates.push({ lat: coordinate[1], lng: coordinate[0]})
    }
    return routeCoordinates;
  }

  function buildPolyline(entry, coordinates) {
    return {
      map: $map,
      path: mapRouteCoordinates(coordinates),
      geodesic: true,
      fillColor: entry.properties.fillColor,
      fillOpacity: entry.properties.fillOpacity,
      strokeColor: entry.properties.strokeColor,
      strokeOpacity: entry.properties.strokeOpacity,
      strokeWeight: entry.properties.strokeWeight,
      type: entry.properties.type,
      title: entry.properties.title
    }
  }

  function createPolygonStringFeature(entry, coordinates) {
    const line = new google.maps.Polygon(buildPolyline(entry, coordinates));
    // Open the InfoWindow on mouseover:
    google.maps.event.addListener(line, 'mouseover', function(e) {
       infoWindow.setPosition(e.latLng);
       infoWindow.setContent("Route " + entry.properties.meansOfTransport + " " + entry.properties.title);
       infoWindow.open($map);
    });

    // Close the InfoWindow on mouseout:
    google.maps.event.addListener(line, 'mouseout', function() {
       infoWindow.close();
    });

    return line;
  }



  onMount(async () => {
    // Create a new Google Maps map
    var mapNew = new google.maps.Map(document.getElementById(mapId), {
      zoom: 5,
      center: { lat: 0, lng: 0 } // Set your desired center coordinates
    });

    map.set(mapNew)

    importGeoJson(geojson);
  });
</script>

<div id="{mapId}" style="height: 1200px;"></div>
