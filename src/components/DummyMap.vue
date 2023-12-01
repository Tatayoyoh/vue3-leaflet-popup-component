<template>
      <l-map ref="map" v-model:zoom="parameters.zoom" v-model:center="parameters.center"
              :useGlobalLeaflet="parameters.useGlobalLeaflet" :options="parameters.options">
              
            <l-tile-layer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png" layer-type="base"></l-tile-layer>

            <l-marker :latLng="[46.16794333707652,24.263992309570316]" >
                <DummyPopup></DummyPopup> <!-- NOT WORKING -->
            </l-marker>
            <!-- Used to show unworking marker postition -->
            <l-circle :latLng="[46.16794333707652,24.263992309570316]" :radius="2000" color="red"></l-circle>


            <l-marker :latLng="[45.98694349643096,24.393768310546875]" >
                <DummyPopup></DummyPopup> <!-- NOT WORKING -->
            </l-marker>
            <!-- Used to show unworking marker postition -->
            <l-circle :latLng="[45.98694349643096,24.393768310546875]" :radius="2000" color="red"></l-circle>


            <l-marker :latLng="[46.22545288226939,24.0380859375]">
                <l-popup>
                    Hello I'm working ! But others markers with component popup do not appear
                </l-popup>
            </l-marker>
    </l-map>
</template>
  
<script setup lang="ts">
    import "leaflet";
    import "leaflet/dist/leaflet.css";
    import { LMap, LTileLayer, LMarker, LPopup, LCircle } from "@vue-leaflet/vue-leaflet";
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
  
  