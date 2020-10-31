<template>
  <div class="px-4 py-10 text-center text-gray-700 dark:text-gray-200">
    <router-view />
    <Footer />
  </div>
</template>

<script setup lang='ts'>
const setupSW = (() => {
  if ("serviceWorker" in navigator)
    navigator.serviceWorker.register("../service-worker.js");
})();
</script>