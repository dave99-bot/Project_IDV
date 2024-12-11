<script>
  import { scaleLinear } from 'd3-scale'
  import { dataNut0 } from './data_Nut0.js'
  import { dataNut2 } from './data_Nut2.js'
  import LeafletMap from './LeafletMap.svelte'
  import LeafletMap2 from './LeafletMap2.svelte'
  import {geoJsonData_prov} from './FeatureCollection.js'
  
  // handle click events for Nut0, 2,3
  const Nut_0 = {dataNut0}
  const Nut_2 = {dataNut2}
  const Nut_3 = {dataNut3}


</script>
<main class = 'map'>
  <div  class= 'title'> 
    <h1>European Map</h1> <LeafletMap/>
    <h1>NUTS 2</h1> <LeafletMap2/> 
    <h1>NUTS 3</h1> <LeafletMap3/> 
  </div>
  <div class = 'northAroow'>
  </div>

  <div class = 'legend'>
  </div>
 <!--Other elements are created by my other group members . The Leaflet JS library was used for the message popups and working with Geojson files which is my part of the final project -->
</main>


<style>


  .title{
    color:black;
    text-align: center
    /**font-family: Arial, sans-serif**/



  }

  .northArrow{

   }
  .scale{

   }

 .lengend{

  }
  

</style>



