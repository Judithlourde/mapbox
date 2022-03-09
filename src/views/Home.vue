<template>
	<div id="map">Home view</div>
</template>

<script>
import mapboxgl from 'mapbox-gl';
export default {
	
	data() {
		return {
			mapbox_id: import.meta.env.VITE_MAPBOX_ID			
		}	
	}, 
	
	mounted() {
		// console.log(this.mapbox_id);
		mapboxgl.accessToken = this.mapbox_id;
		const map = new mapboxgl.Map({
			container: 'map', // container ID
			style: 'mapbox://styles/mapbox/streets-v11', // style URL
			center: [10.73, 59.91], // starting position [lng, lat]
			zoom: 15 // starting zoom
		});

		// mapboxgl.accessToken = 'pk.eyJ1IjoianVkaXRocGV0ZXIiLCJhIjoiY2wwZ2Zpa2RrMTJpcDNjcXRwbmYxenpiMyJ9.D4zoWLd-CJlmV2ojxd824Q';
		const geojson = {
			'type': 'FeatureCollection',
			'features': [
				{
					'type': 'Feature',
					'properties': {
					'message': 'Foo',
					'iconSize': [60, 60]
				},
					'geometry': {
					'type': 'Point',
					'coordinates': [-66.324462, -16.024695]
				}
			},
			{
				'type': 'Feature',
				'properties': {
					'message': 'Bar',
					'iconSize': [50, 50]
				},
				'geometry': {
					'type': 'Point',
					'coordinates': [-61.21582, -15.971891]
				}
			},
			{
				'type': 'Feature',
				'properties': {
					'message': 'Baz',
					'iconSize': [40, 40]
				},
				'geometry': {
					'type': 'Point',
					'coordinates': [-63.292236, -18.281518]
				}
			}
		]
		};

		
 		
	},

	created() {
		this.fetchGeoCode();
	},

	methods: {
		async fetchGeoCode() {
            navigator.geolocation.getCurrentPosition(position => {
				console.log(position); 
            });
        },
	},
}
</script>

<style>
	#map {
		width: 100%;
		height: 500px;
	}
</style>

