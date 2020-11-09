<template>
  <h1 class="mb-6">Notification settings</h1>
  <ul class="flex justify-around">
    <li
      v-for="{type, name, active} in notificationTypes"
      :key="type"
    >

      <input
        type="checkbox"
        :id="type"
        class="mr-2 leading-tight"
        v-model="settings.type"
        :value="type"
      >

      <label :for="type">{{ name }}</label>
    </li>
  </ul>
</template>
<script setup lang='ts'>
import { reactive } from "vue";

export const notificationTypes = [
  { type: "bh", name: "Blue Hour", active: false },
  { type: "gh", name: "Golden Hour", active: false },
];

export const settings = reactive({
  type: [],
});
</script>
