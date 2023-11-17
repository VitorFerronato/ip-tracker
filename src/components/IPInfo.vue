<template>
  <div
    class="absolute -bottom-64 lg:-bottom-20 flex fle-col lg:flex-row bg-white gap-y-4 gap-x-12 px-8 pt-8 pb-12 rouded-md"
  >
    <div class="flex flex-col">
      <h3 class="text-xs mb-2 uppercase">IP Address</h3>
      <span class="text-2xl">8.8.8.8</span>
    </div>

    <div class="flex flex-col">
      <h3 class="text-xs mb-2 uppercase">Location</h3>
      <span class="text-2xl">Michigan</span>
    </div>

    <div class="flex flex-col">
      <h3 class="text-xs mb-2 uppercase">Timezone</h3>
      <span class="text-2xl">UTC -07:00</span>
    </div>

    <div class="flex flex-col">
      <h3 class="text-xs mb-2 uppercase">Isp</h3>
      <span class="text-2xl">Google</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      token:
        "pk.eyJ1Ijoidml0b3JmZXJyb25hdG8iLCJhIjoiY2xwMjFkc3I0MG43NjJqcXZ1Yjd6djA5dyJ9.M0ATxtL-4nskEtag8w6vpA",
    };
  },
};
</script>