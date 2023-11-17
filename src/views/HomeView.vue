<template>
  <div class="flex flex-col h-screen max-h-screen">
    <div
      class="flex justify-center relative bg-hero-pattern bg-cover px-4 pt-8 pb-32"
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
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
};
</script>
