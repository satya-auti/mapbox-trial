<template>
  <div>
    <h1>Map Installation</h1>
  </div>
  <VMap :accessToken="accessToken" :mapStyle="mapStyle" />
</template>

<script>
import "mapbox-gl/dist/mapbox-gl.css";
import mapbox from "mapbox-gl";
// import VMap from "v-mapbox";
// import { reactive } from "vue";
import { VMap } from "v-mapbox";

export default {
  components: {
    VMap,
  },
  data() {
    return {
      accessToken:
        "pk.eyJ1Ijoic2F0eWEtYXV0aSIsImEiOiJjbDZnYm9qYmMwYXF0M2VvNmJtMHVjdjlsIn0.zRsVf1aqfOgA_fovyLs6UA", // your access token. Needed if you using Mapbox maps
      mapStyle: MAP_STYLE, // your map style
    };
  },

  created() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = mapbox;
  },
};

import mapboxgl from "mapbox-gl"; // or "const mapboxgl = require('mapbox-gl');"

// TO MAKE THE MAP APPEAR YOU MUST
// ADD YOUR ACCESS TOKEN FROM
// https://account.mapbox.com

// mapboxgl.accessToken = '<your access token here>';
mapboxgl.accessToken =
  "pk.eyJ1Ijoic2F0eWEtYXV0aSIsImEiOiJjbDZnYm9qYmMwYXF0M2VvNmJtMHVjdjlsIn0.zRsVf1aqfOgA_fovyLs6UA";
const map = new mapboxgl.Map({
  container: "map", // container ID
  style: "mapbox://styles/mapbox/streets-v11", // style URL
  center: [-74.5, 40], // starting position [lng, lat]
  zoom: 9, // starting zoom
  projection: "globe", // display the map as a 3D globe
});
map.on("style.load", () => {
  map.setFog({}); // Set the default atmosphere style
});
</script>
