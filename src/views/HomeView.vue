<template>
  <div class="flex flex-col h-screen max-h-screen">
    <div
      class="z-20 flex justify-center relative bg-hero-pattern bg-cover px-4 pt-8 pb-32"
    >
      <!-- Search -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text-white text-center text-3xl pb-4">IP Adress Tracker</h1>
        <div class="flex">
          <input
            class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
            placeholder="Search for any IP address or leave empty to get your ip info"
            type="text"
          />
          <i
            class="cursor-pointer bg-black text-white px-4 rounded-tr-md rounded-br-md flex items-center fa-solid fa-chevron-right"
          ></i>
        </div>
      </div>

      <!-- IP info -->
      <IPInfo />
    </div>

    <!-- map -->
    <div id="map" class="h-full z-10"></div>
  </div>
</template>

<script>
import IPInfo from "@/components/IPInfo.vue";
import { onMounted } from "vue";
import leaflet from "leaflet";
// @ is an alias to /src

export default {
  components: { IPInfo },
  name: "HomeView",
  setup() {
    let myMap;

    onMounted(() => {
      myMap = leaflet.map("map").setView([51.505, -0.09], 13);

      leaflet
        .tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
          maxZoom: 19,
          attribution:
            '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
        })
        .addTo(myMap);
    });
  },
};
</script>
