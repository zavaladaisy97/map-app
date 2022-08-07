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
      // create the popup
      const popup = new mapboxgl.Popup({ offset: 25 }).setText("here is my house");
      // Create a default Marker
      const marker1 = new mapboxgl.Marker().setLngLat([-101.412, 20.003]).setPopup(popup).addTo(map);

      map.on("style.load", () => {
        map.setFog({}); // Set the default atmosphere style
      });
      console.log(marker1, popup);
    },
  },
};
</script>

<style scoped>
#map {
  height: 500px;
  width: 500px;
  margin-left: 100px;
}
</style>
