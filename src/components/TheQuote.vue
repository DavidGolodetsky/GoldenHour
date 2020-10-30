<template>
  <blockquote v-if="quote">
    <p>{{ quote.text }}</p>
    <footer> — {{ quote.author }}</footer>
  </blockquote>
</template>

<script>
import quotes from '../data/quotes.json'
import { ref } from 'vue'

export default {
  setup () {

    let quote = ref(null)

    const getQuote = (() => {
      const quotesArr = JSON.parse(JSON.stringify(quotes))
      quote = quotesArr[Math.floor(Math.random() * quotesArr.length)]
    })()

    return { quote }
  },
}
</script>

