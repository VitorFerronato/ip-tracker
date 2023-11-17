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
            v-model="queryIp"
            class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
            placeholder="Search for any IP address or leave empty to get your ip info"
            type="text"
          />
          <i
            @click="getIpInfo"
            class="cursor-pointer bg-black text-white px-4 rounded-tr-md rounded-br-md flex items-center fa-solid fa-chevron-right"
          ></i>
        </div>
      </div>

      <!-- IP info -->
      <IPInfo v-if="ipInfo" :ipInfo="ipInfo" />
    </div>

    <!-- map -->
    <div id="map" class="h-full z-10"></div>
  </div>
</template>

<script>
import IPInfo from "@/components/IPInfo.vue";
import { onMounted, ref } from "vue";
import leaflet from "leaflet";
import axios from "axios";
// @ is an alias to /src

export default {
  components: { IPInfo },
  name: "HomeView",
  setup() {
    let myMap;
    const queryIp = ref("");
    const ipInfo = ref(null);

    onMounted(() => {
      myMap = leaflet.map("map").setView([51.505, -0.09], 9);

      leaflet
        .tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
          maxZoom: 19,
          attribution:
            '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
        })
        .addTo(myMap);
    });

    const getIpInfo = async () => {
      try {
        const data = await axios.get(`http://ip-api.com/json/${queryIp.value}`);
        const result = data?.data ?? [];

        ipInfo.value = {
          address: result.query,
          state: result.country,
          timezone: result.timezone,
          isp: result.isp,
          lat: result.lat,
          lon: result.lon,
        };

        leaflet.marker([ipInfo.value.lat, ipInfo.value.lon]).addTo(myMap);
        myMap.setView([ipInfo.value.lat, ipInfo.value.lon], 11);
      } catch (error) {
        alert(error.message);
      }
    };

    return { queryIp, ipInfo, getIpInfo };
  },
};
</script>
