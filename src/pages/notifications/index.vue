<template>
  <h1 class="mb-6">Notification settings</h1>
  <ul class="flex justify-around w-1/2 mx-auto mb-8">
    <li
      v-for="notification in notificationTypes"
      :key="notification.type"
    >

      <input
        type="checkbox"
        :id="notification.type"
        class="mr-2 leading-tight"
        v-model="notification.active"
        :value="notification.type"
      >

      <label :for="notification.type">{{ notification.name }}</label>
    </li>
  </ul>
  <div class="flex justify-center">
    <button
      type="button"
      @click="setNotifications"
      class="border border-red-500   text-white rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-red-400 focus:outline-none focus:shadow-outline"
    >
      Submit
    </button>
  </div>
  {{notificationSetted}}
  <teleport
    to="#the-header"
    v-if="notificationSetted"
  >
    <Icon
      class="iconify inline-block"
      icon="carbon:notification"
    />
  </teleport>
</template>
<script setup lang='ts'>
import { reactive } from "vue";
import { ref } from "vue";

export let notificationSetted = ref(false);

export const notificationTypes = [
  { type: "bh", name: "Blue Hour", active: false },
  { type: "gh", name: "Golden Hour", active: false },
];

export const setNotifications = () => {
  console.log("awd");
  notificationSetted.value = true;
};

export const settings = reactive({
  type: [],
});
</script>
