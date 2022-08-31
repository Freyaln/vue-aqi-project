<template>
  <div id="mapContainer" class="globe-map"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";

export default {
  name: "WorldMap",
  data() {
    return {
      accessToken: import.meta.env.VITE_MAPBOX_KEY,
    };
  },
  mounted() {
    mapboxgl.accessToken = this.accessToken;

    const map = new mapboxgl.Map({
      container: "mapContainer",
      style: "mapbox://styles/mapbox/streets-v11",
      center: [7.14, 46.8],
      zoom: 5,
      minZoom: 5,
      projection: "globe",
    });

    const marker = new mapboxgl.Marker().setLngLat([3.87, 43.59]).addTo(map);

    const navigationButtons = new mapboxgl.NavigationControl();

    const geolocate = new mapboxgl.GeolocateControl({
      positionOptions: {
        enableHighAccuracy: true,
      },
      trackUserLocation: true,
    });

    map.addControl(geolocate, "bottom-right");
    map.addControl(navigationButtons, "bottom-right");
  },
};
//
</script>

<style lang="scss">
.globe-map {
  height: 100%;
}
</style>
