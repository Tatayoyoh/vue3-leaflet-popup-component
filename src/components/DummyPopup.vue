<template>
    <l-popup>
      <div :innerHTML="text"></div>
    </l-popup>
</template>

<script setup lang="ts">
  import { LPopup } from "@vue-leaflet/vue-leaflet";
  defineProps({
      text: {
          type: String,
          required: true
      }
  });
</script>

<style scoped>
</style>