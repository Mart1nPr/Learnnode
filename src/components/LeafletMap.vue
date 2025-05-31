<script setup>
import L from "leaflet";
import { onMounted, useId, watch } from "vue";
import "leaflet/dist/leaflet.css";
import "leaflet/dist/images/marker-icon-2x.png";
import "leaflet/dist/images/marker-shadow.png";

const { center, zoom } = defineProps(["center", "zoom"]);
const id = "map-" + useId();
let map;

onMounted(() => {
  map = L.map(id).setView(center, zoom);
  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }).addTo(map);

  var marker = L.marker([59.42686, 24.74353]).addTo(map);
  var marker = L.marker([59.415851, 24.799275]).addTo(map);

  var polygon = L.polygon([
    [59.415524, 24.798830],
    [59.417379, 24.798878],
    [59.417376, 24.799823],
    [59.416539, 24.799817],
    [59.416474, 24.803604],
    [59.416285, 24.803615],
    [59.416250, 24.799806],
    [59.415516, 24.799790],
  ]).addTo(map);
});
watch(
  () => center,
  (center, oldCenter) => {
    map.panTo(center);
  }
);
watch(
  () => zoom,
  (zoom) => {
    map.setZoom(zoom);
  }
);
</script>
<template>
  <div :id="id"></div>
</template>
<style scoped>
div {
  height: 90vh;
}
</style>
