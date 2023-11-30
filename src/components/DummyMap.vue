<template>
      <l-map ref="map" v-model:zoom="parameters.zoom" v-model:center="parameters.center"
              :useGlobalLeaflet="parameters.useGlobalLeaflet" :options="parameters.options">
              
            <l-tile-layer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png" layer-type="base"></l-tile-layer>

            <l-marker :latLng="[46.22545288226939,19.291992187500004]" >
                <!-- NOT WORKING -->
                <DummyPopup></DummyPopup>
            </l-marker>

            <l-marker :latLng="[43.29320031385285,23.466796875000004]" >
                <!-- NOT WORKING -->
                <DummyPopup></DummyPopup>
            </l-marker>

            <l-marker :latLng="[46.22545288226939,24.0380859375]">
                <l-popup>
                    Hello I'm working ! But not others :(
                </l-popup>
            </l-marker>
    </l-map>
</template>
  
<script setup lang="ts">
    import "leaflet";
    import "leaflet/dist/leaflet.css";
    import { LMap, LTileLayer, LMarker, LPopup } from "@vue-leaflet/vue-leaflet";
    import { ref } from "vue";
    import DummyPopup from '@/components/DummyPopup.vue'


    const map = ref()
  
    const props = defineProps({
          parameters: {
              type: Object,
              default: {
                  center: [45.706179285330855,22.280273437500004], // centered on Europe by default
                  zoom: 6,
                  useGlobalLeaflet: false,
                  options: {zoomControl: false}
              }
          },
      });
</script>
  
  