<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id="map"></div>
    <button id="pause"></button>

  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}
</style>
<style>
button {
  position: absolute;
  margin: 20px;
}

#pause::after {
  content: "Pause";
}

#pause.pause::after {
  content: "Play";
}
</style>
<script>
/* global mapboxgl */
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_KEY;
    var map = new mapboxgl.Map({
      container: "map", // container id
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-87.6298, 41.8781], // starting position [lng, lat]
      zoom: 9, // starting zoom
    });
    var marker = new mapboxgl.Marker().setLngLat([-87.6298, 41.8781]).addTo(map);

    var geojson = {
      type: "FeatureCollection",
      features: [
        {
          type: "Feature",
          geometry: {
            type: "LineString",
            coordinates: [[-87.6298, 41.8781]],
          },
        },
      ],
    };
    var speedFactor = 30; // number of frames per longitude degree
    var animation; // to store and cancel the animation
    var startTime = 0;
    var progress = 0; // progress = timestamp - startTime
    var resetTime = false; // indicator of whether time reset is needed for the animation
    var pauseButton = document.getElementById("pause");
  },

  methods: {},
};
</script>