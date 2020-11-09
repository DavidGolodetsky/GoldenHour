<template>
  <div class="px-4 py-10 text-center text-gray-600 dark:text-gray-300">
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

