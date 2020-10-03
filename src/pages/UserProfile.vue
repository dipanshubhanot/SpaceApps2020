<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-12">
          <card>
            <template slot="header">
              <h3 class="card-title" align="center">
                Simulating Forest Spread
              </h3>
            </template>
            <template> </template>
            <template>
              <gmap-map
                id="map"
                :center="myCoords"
                :zoom="12"
                :options="options"
                map-type-id="terrain"
                ref="mapRef"
              >
                <!-- <div v-for="location in locations">
                  <gmap-marker
                    :position="location.coords"
                    icon="https://www.flaticon.com/svg/static/icons/svg/394/394631.svg"
                  >
                  </gmap-marker>
                </div> -->
                <gmap-polygon
                  :key="index"
                  v-for="(m, index) in layers"
                  :paths="m.paths"
                  @click="toggleInfoWindow(m, index)"
                >
                </gmap-polygon>

                <gmap-info-window
                  :position="infoWindow.pos"
                  :opened="infoWindow.open"
                  @closeclick="infoWindow.open = false"
                >
                  <div v-html="infoWindow.template"></div>
                </gmap-info-window>
              </gmap-map>
            </template>
            <template slot="footer">
              <hr />
              <div class="stats">
                <i class="fa fa-history"></i> Updated 3 minutes ago
              </div>
            </template>
          </card>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Card from "src/components/Cards/Card.vue";
import { API_KEY } from "./Maps/API_KEY";
import Vue from "vue";
import * as VueGoogleMaps from "vue2-google-maps";
// import currPos from "../main.js";
Vue.use(VueGoogleMaps, {
  load: {
    key: API_KEY,
  },
  installComponents: true,
});
var location = {
  coords: {
    latitude: 0,
    longitude: 0,
  },
};

export default {
  data() {
    return {
      paths: [
        [
          { lng: 142.22900390624997, lat: -38.59970036588819 },
          { lng: 147.5244140625, lat: -38.59970036588819 },
          { lng: 147.5244140625, lat: -35.97800618085566 },
          { lng: 142.22900390624997, lat: -35.97800618085566 },
          { lng: 142.22900390624997, lat: -38.59970036588819 },
        ],
      ],
      layers: [
        {
          paths: [
            [
              { lng: 142.22900390624997, lat: -38.59970036588819 },
              { lng: 147.5244140625, lat: -38.59970036588819 },
              { lng: 147.5244140625, lat: -35.97800618085566 },
              { lng: 142.22900390624997, lat: -35.97800618085566 },
              { lng: 142.22900390624997, lat: -38.59970036588819 },
            ],
          ],
          desc: "Lulwa ho ke?",
          options: {
            fillColor: "#570188",
          },
        },
      ],
      infoWindow: {
        pos: {
          lat: 0,
          lng: 0,
        },
        open: false,
        template:''
      },
      myCoords: {
        lng: 0,
        lat: 0,
        // lat: 0,
        // lng: 0,
      },
      polyOptions: {
        fillColor: "#FF0000",
      },
      options: {
        styles: [
          {
            featureType: "water",
            stylers: [
              { saturation: 43 },
              { lightness: -11 },
              { hue: "#0088ff" },
            ],
          },
          {
            featureType: "road",
            elementType: "geometry.fill",
            stylers: [
              { hue: "#ff0000" },
              { saturation: -100 },
              { lightness: 99 },
            ],
          },
          {
            featureType: "road",
            elementType: "geometry.stroke",
            stylers: [{ color: "#808080" }, { lightness: 54 }],
          },
          {
            featureType: "landscape.man_made",
            elementType: "geometry.fill",
            stylers: [{ color: "#ece2d9" }],
          },
          {
            featureType: "poi.park",
            elementType: "geometry.fill",
            stylers: [{ color: "#ccdca1" }],
          },
          {
            featureType: "road",
            elementType: "labels.text.fill",
            stylers: [{ color: "#767676" }],
          },
          {
            featureType: "road",
            elementType: "labels.text.stroke",
            stylers: [{ color: "#ffffff" }],
          },
          { featureType: "poi", stylers: [{ visibility: "off" }] },
          {
            featureType: "landscape.natural",
            elementType: "geometry.fill",
            stylers: [{ visibility: "on" }, { color: "#b8cb93" }],
          },
          { featureType: "poi.park", stylers: [{ visibility: "on" }] },
          {
            featureType: "poi.sports_complex",
            stylers: [{ visibility: "on" }],
          },
          { featureType: "poi.medical", stylers: [{ visibility: "on" }] },
          {
            featureType: "poi.business",
            stylers: [{ visibility: "simplified" }],
          },
        ],
      },
      editTooltip: "Edit Task",
      deleteTooltip: "Remove",
      currentMidx:null
    };
  },

  components: {
    Card,
  },
  created() {
    this.fireData = [
      {
        coords: { lat: -37.835787, lng: 144.977852 },
        zones: {
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Polygon",
                coordinates: [
                  [
                    { lat: 142.22900390624997, lng: -38.59970036588819 },
                    { lat: 147.5244140625, lng: -38.59970036588819 },
                    { lat: 147.5244140625, lng: -35.97800618085566 },
                    { lat: 142.22900390624997, lng: -35.97800618085566 },
                    { lat: 142.22900390624997, lng: -38.59970036588819 },
                  ],
                ],
              },
            },
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Polygon",
                coordinates: [
                  [
                    [142.5146484375, -35.15584570226543],
                    [143.19580078124997, -34.30714385628803],
                    [142.62451171875, -34.33436448702629],
                    [141.6796875, -34.651285198954135],
                    [140.767822265625, -34.91296249521695],
                    [142.371826171875, -35.52328517910781],
                    [143.448486328125, -35.56798045801208],
                    [143.909912109375, -35.02099970111467],
                    [143.26171875, -34.624167789904895],
                    [142.5146484375, -35.15584570226543],
                  ],
                ],
              },
            },
          ],
        },
      },
      {
        coords: { lat: -37.813211, lng: 144.943005 },
      },
      {
        coords: { lat: -37.83755, lng: 144.945494 },
      },
    ];
    this.myCoords = this.fireData[0].coords;
    this.locations = this.fireData;
  },
  methods: {
    toggleInfoWindow: function (marker, idx) {
      this.infoWindow.pos = marker.paths[0][0];
      this.infoWindow.template = this.getInfoWindowContent(marker);

      //check if its the same marker that was selected if yes toggle
      if (this.currentMidx == idx) {
        this.infoWindow.open = !this.infoWindow.open;
      }
      //if different marker set infowindow to open and reset current marker index
      else {
        this.infoWindow.open = true;
        this.currentMidx = idx;
      }
    },

    getInfoWindowContent: function (marker) {
      return `<card>
  <div>
    <div >
      <div>
        <p>Zone Level</p>
      </div>
    </div>
    <div>
      ${marker.desc}
      <br>

    </div>
  </div>
</card>`;
    },
  },
};
</script>
<style>
#map {
  min-height: calc(100vh - 123px);
}
</style>

