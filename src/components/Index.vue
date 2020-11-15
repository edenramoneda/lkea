
<template>
  <v-app id="inspire">
    <v-app-bar
      color="deep-purple accent-4"
      dark
      prominent
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>My files</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-filter</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>
    <div style="height: 80vh; width: 100%">
      <l-map
        style="height: 80vh; width: 100%"
        :zoom="zoom"
        :maxZoom="maxZoom"
        :center="center"
        :minZoom="minZoom"
        :bounds="bounds"
        :max-bounds="maxBounds"
        :attributionControl="attributionControl"
        :maxBoundsViscosity="maxBoundsViscosity"
        @update:zoom="zoomUpdated"
        @update:center="centerUpdated"
        @update:bounds="boundsUpdated"
      >
        <l-tile-layer :url="url" :noWrap="noWrap" :attributionControl="attributionControl"></l-tile-layer>
      </l-map>
    </div>
  </v-app>
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
        attributionControl: false,
        links: [
          'Dashboard',
          'Messages',
          'Profile',
          'Updates',
        ],
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
