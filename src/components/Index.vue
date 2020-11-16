
/*eslint-disable */
// eslint-disable-next-line
<template>
  <v-app id="inspire">
    <v-app-bar
      class="lkea-bg-color lkea-header-nav"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-spacer/><v-spacer/>
    
      <div class="lkea-btn-link" tile>
         <v-btn icon
        >
          <v-icon>mdi-map-marker</v-icon>
          <p>stores</p>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-account</v-icon>
          <p>sign in</p>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-cart</v-icon>
          <p>cart</p>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
          <p>search</p>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
          <p>more</p>
        </v-btn>
      </div>
    </v-app-bar>
      <v-toolbar-title class="company-name text-center">
        <h1><b>IKEA</b></h1>
      </v-toolbar-title>

      <l-map
        style="height: 80vh; width: 100%;margin-top:-5rem"
        :zoom="zoom"
        :maxZoom="maxZoom"
        :center="center"
        :minZoom="minZoom"
        :bounds="bounds"
        :max-bounds="maxBounds"
        :attributionControl="attributionControl"
        :maxBoundsViscosity="maxBoundsViscosity"
        :id="id"
        @update:zoom="zoomUpdated"
        @update:center="centerUpdated"
        @update:bounds="boundsUpdated"
      >
        <l-tile-layer :url="url" :noWrap="noWrap" :attributionControl="attributionControl"></l-tile-layer>
      </l-map>
      <h4 class="lkea-map-note">If you are not in the United States, please select your location</h4>
      <div class="lkea-slideshow">
        <v-carousel style="height:60vh">
          <v-carousel-item
            v-for="(simgs,i) in slideshow_img"
            :key="i"
            :src="simgs.src"
            reverse-transition="fade-transition"
            transition="fade-transition"
            style="height:60vh"
          ></v-carousel-item>
        </v-carousel>
      </div>
      <div class="gallery-1">
        <v-row no-gutters>
          <v-col
            v-for="(g,i) in gallery"
            :key="i"
            cols="12"
            sm="4"
            
          >
            <v-img :src="g.src" class="gal-img"></v-img>
          </v-col>
        </v-row>
      </div>
       <div class="gallery-1">
        <v-row no-gutters>
          <v-col
            v-for="(g,i) in interiors"
            :key="i"
            sm="4"
            md="3"
          >
           <v-img :src="g.src" class="gal-img"></v-img>
          </v-col>
        </v-row>
      </div>
  </v-app>
</template>

<script>
/* eslint-disable */
// eslint-disable-next-line
import { latLngBounds, latLng } from "leaflet";
export default {
    
    data () {
      return {
        url: 'https://api.mapbox.com/styles/v1/mapbox/light-v9/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoiZWRlbnJhbW9uZWRhIiwiYSI6ImNraGo5YjR2OTExMnQyd25xdmkzdjN3bWsifQ.GlWzmLUylIA31m0J-ytxdQ',
        zoom: 3,
        center: [47.413220, -1.219482],
        maxZoom: 20,
        minZoom: 3,
        noWrap: true,
        maxBoundsViscosity: 1.0,
        bounds: null,
        maxBounds: latLngBounds([
          [-84.72233856539854, -180],
          [85.06500754829302, 180.17578125]
        ]),
        attributionControl: false,
        id: 'mapbox/light-v9',
        links: [
          'Dashboard',
          'Messages',
          'Profile',
          'Updates',
        ],
        slideshow_img: [
          {
            src: require('@/assets/uploads/bedroom1.jpg'),
          },
          {
            src: require('@/assets/uploads/bedroom1.jpg'),
          },
          {
            src: require('@/assets/uploads/bedroom1.jpg'),
          },
          {
            src: require('@/assets/uploads/bedroom1.jpg'),
          },
        ],
        gallery: [
          {
            src: require('@/assets/uploads/kitchen.jpg'),
          },
          {
            src: require('@/assets/uploads/bedroom-closet-3.jpg'),
          },
          {
            src: require('@/assets/uploads/b4.jpg'),
          },
        ],
        interiors: [
          {
            src: require('@/assets/uploads/livingroom.jpg'),
          },
          {
            src: require('@/assets/uploads/bedroom4.jpg'),
          },
          {
            src: require('@/assets/uploads/bathroom.jpg'),
          },
          {
            src: require('@/assets/uploads/kitchen2.jpg'),
          },
          {
            src: require('@/assets/uploads/dining.jpg'),
          },
          {
            src: require('@/assets/uploads/textile.jpg'),
          },
          {
            src: require('@/assets/uploads/business.jpg'),
          },
          {
            src: require('@/assets/uploads/outdoor.jpg'),
          },
        ]
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
