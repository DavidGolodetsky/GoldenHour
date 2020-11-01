<template>
  <blockquote v-if="quote">
    <p>{{ quote.text }}</p>
    <footer> — {{ quote.author }}</footer>
  </blockquote>
</template>

<script setup lang='ts'>
import quotes from "/~/data/quotes.json";
import { ref } from "vue";

export let quote = ref(null);

const getQuote = (() => {
  const quotesArr = JSON.parse(JSON.stringify(quotes));
  quote = quotesArr[Math.floor(Math.random() * quotesArr.length)];
})();
</script>

