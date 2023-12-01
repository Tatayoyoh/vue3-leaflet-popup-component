<template>
      <l-map ref="map" v-model:zoom="parameters.zoom" v-model:center="parameters.center"
              :useGlobalLeaflet="parameters.useGlobalLeaflet" :options="parameters.options">
              
            <l-tile-layer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png" layer-type="base"></l-tile-layer>
            

            <!-- NOT WORKING -->
            <l-marker :latLng="[45.98694349643096,24.393768310546875]" >
                <DummyPopup text="Hello I'm NOT working<br>My Marker is not showing :("></DummyPopup>
            </l-marker>
            <!-- Red circle is used to show unworking marker postition -->
            <l-circle :latLng="[45.98694349643096,24.393768310546875]" :radius="2000" color="red"></l-circle>


            <!-- WORKAROUND set icon manually -->
            <l-marker :latLng="[46.187912147928145,24.327163696289066]" >
                <l-icon :icon-size="[48,48]" :icon-anchor="[24,48]" icon-url="start.svg" ></l-icon>
                <DummyPopup text="Hello I'm the workaround !"></DummyPopup>
            </l-marker>

            <!-- NORMAL USAGEs -->
            <l-marker :latLng="[46.214050815339526,24.16648864746094]">
                <l-popup>Hello I'm working ! But others markers with component popup do not appear</l-popup>
            </l-marker>
    </l-map>
</template>
  
<script setup lang="ts">
    import "leaflet";
    import "leaflet/dist/leaflet.css";
    import { LMap, LTileLayer, LMarker, LPopup, LCircle, LIcon } from "@vue-leaflet/vue-leaflet";
    import { ref } from "vue";
    import DummyPopup from '@/components/DummyPopup.vue'

    const iconSize = 32;
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

    function dynamicSize () {
      return [iconSize, iconSize * 1.15];
    }

    function dynamicAnchor () {
        return [iconSize / 2, iconSize * 1.15];
    }
</script>
  
  