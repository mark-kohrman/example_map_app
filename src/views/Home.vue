<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id="map"></div>

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
      center: [-77.5, 34], // starting position [lng, lat]
      zoom: 9, // starting zoom
    });
  },
  methods: {},
};
</script>