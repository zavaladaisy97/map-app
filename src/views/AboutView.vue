<template>
  <div class="about">
    <h1>map time</h1>
    <div id="map"></div>
  </div>
</template>

<script>
/* global mapboxgl */

export default {
  data: function () {
    return {};
  },
  created: function () {},
  mounted: function () {
    this.showMap();
  },
  methods: {
    showMap: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MY_MAP_KEY;
      const map = new mapboxgl.Map({
        container: "map", // container ID
        style: "mapbox://styles/mapbox/streets-v11", // style URL
        center: [-101.4167, 20.0027], // starting position [lng, lat]
        zoom: 9, // starting zoom
        projection: "globe", // display the map as a 3D globe
      });

      map.on("style.load", () => {
        map.setFog({}); // Set the default atmosphere style
      });
    },
  },
};
</script>

<style scoped>
#map {
  height: 300px;
  width: 500px;
  margin-left: 25px;
}
</style>
