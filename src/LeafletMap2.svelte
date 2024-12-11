
<script>
    import { dataNut0 } from './data_Nut0.js'
    import { dataNut2 } from './data_Nut2.js'
    import { dataNut3 } from './data_Nut3.js'
    import {geoJsonData2} from './FeatureCollection2.js'
    import { onMount } from 'svelte';
    import L from 'leaflet';
    import 'leaflet/dist/leaflet.css';

    let mapElement2;

    onMount(() => {
        const map = L.map(mapElement2).setView([54, 15], 4); // Centered on Europe

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '© OpenStreetMap contributors'
        }).addTo(map);

        //Load the GeoJSON file from Feature .js
        L.geoJson(geoJsonData2, { 
            style: function (feature) { 
                return { 
                    color: 'blue',  weight: 1
                };
            },
            onEachFeature: function (feature, layer) {
                // Bind popup on click event. Have to add nut2 and 3 when the geometry is added 
                layer.on('click', function () {
                    const country2 = feature.properties.NUTS_ID
                     // find matching internet speeds 
                    const countryData = dataNut2.find(item => item.id ===country2)
                    

                    if (countryData){
                        const{ avg_u, avg_d, avg_l,name} =countryData
                        layer.bindPopup(` 
                            <strong>Name:</strong> ${name}<br>
                            <strong>Population:</strong> ${feature.properties.POP2005}(2005)<br>
                            <strong>Area:</strong> ${feature.properties.AREA} <br>
                            <strong>Upload:</strong>${avg_u}Mbps<br>
                            <strong>Download:</strong>${avg_d}Mbps<br>
                            <strong>Latency:</strong>${avg_l} ms <br>
                        `).openPopup();
                    } else {
                        layer.bindPopup(` 
                            <strong>Name:</strong> ${feature.properties.NAME}<br>
                            <strong>Population:</strong> ${feature.properties.POP2005}<br>
                            <strong>Area:</strong> ${feature.properties.AREA} <br>
                        `).openPopup();
                    }
                    
                 });
            }
        }).addTo(map);
    });

</script>

<style>
  div {      
    height: 800px; /* Adjust the height*/
  }
</style>

<div bind:this={mapElement2}></div>
