
<template>
     <div style="height: 80vh; width: 100%">
      <div class="info" style="height: 15%">
        <span>Center: {{ center }}</span>
        <span>Zoom: {{ zoom }}</span>
        <span>Bounds: {{ bounds }}</span>
      </div>
      <l-map
        style="height: 80vh; width: 100%"
        :zoom="zoom"
        :maxZoom="maxZoom"
        :center="center"
        :minZoom="minZoom"
        :bounds="bounds"
        :max-bounds="maxBounds"
        :maxBoundsViscosity="maxBoundsViscosity"
        @update:zoom="zoomUpdated"
        @update:center="centerUpdated"
        @update:bounds="boundsUpdated"
      >
        <l-tile-layer :url="url" :noWrap="noWrap"></l-tile-layer>
      </l-map>
  </div>
</template>

<script>
/* eslint-disable */
import { latLngBounds, latLng } from "leaflet";
export default {
    
    data () {
      return {
        url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
        zoom: 3,
        center: [47.413220, -1.219482],
        maxZoom: 3,
        minZoom: 3,
        noWrap: true,
        maxBoundsViscosity: 1.0,
        bounds: null,
        maxBounds: latLngBounds([
          [-84.72233856539854, -180],
          [85.06500754829302, 180.17578125]
        ]),
      };
    },
    methods: {
      doSomethingOnReady() {
        this.map = this.$refs.myMap.mapObject
      },
       zoomUpdated (zoom) {
      this.zoom = zoom;
      },
      centerUpdated (center) {
        this.center = center;
      },
      boundsUpdated (bounds) {
        this.bounds = bounds;
      }
    }
}

</script>
