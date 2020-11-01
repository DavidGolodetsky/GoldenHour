<template>
  <div
    v-if="sunPosition"
    class="flex justify-around max-w-md mx-auto"
  >
    <div>
      <h3>Sunrise:</h3>
      <div> {{ sunPosition.sunrise }}</div>
    </div>
    <div>
      <h3>Sunset:</h3>
      <div> {{ sunPosition.sunset }}</div>
    </div>
  </div>

  <!-- TODO:handle loading with Suspense -->
  <span
    v-else
    class="relative animate-ping inline-flex rounded-full h-3 w-3 bg-red-500"
  ></span>
</template>

<script setup lang='ts'>
import axios from "axios";
import { ref } from "vue";

export let sunPosition = ref(null);

const getLocation = (() => {
  if (!navigator.geolocation) {
    alert("Geolocation is not supported by your browser");
  } else {
    navigator.geolocation.getCurrentPosition(
      (position) => {
        const lat = position.coords.latitude;
        const long = position.coords.longitude;
        return axios
          .get(`https://api.sunrise-sunset.org/json?lat=${lat}&lng=-${long}`)
          .then((res) => (sunPosition.value = res.data.results))
          .catch((err) => console.log(err));
      },
      (err) => console.log(err)
    );
  }
})();
</script>
