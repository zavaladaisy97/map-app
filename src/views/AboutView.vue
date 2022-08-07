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
    return {
      places: [],
    };
  },
  created: function () {},
  mounted: function () {
    this.placesIndex();
  },
  methods: {
    placesIndex: function () {
      //this is where we make an API call to backend
      this.places = [
        { lat: -25.363, lng: 131.044, description: "A place in Australia" },
        { lat: -33.8675, lng: 151.207, description: "The main city!" },
      ];
      this.showMap();
    },

    showMap: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MY_MAP_KEY;
      const map = new mapboxgl.Map({
        container: "map", // container ID
        style: "mapbox://styles/mapbox/light-v10", // style URL
        center: [this.places[0].lng, this.places[0].lat], // starting position [lng, lat]
        zoom: 9, // starting zoom
        projection: "globe", // display the map as a 3D globe
      });

      this.places.forEach((place) => {
        let popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
        let marker = new mapboxgl.Marker().setLngLat([place.lng, place.lat]).setPopup(popup).addTo(map);
        console.log(marker);
      });
    },
  },
};
</script>

<style scoped>
#map {
  height: 750px;
  width: 750px;
  margin-left: 25px;
}
</style>
