<template>
  <div id="app">
    <h1 class="text-5xl font-bold">Study Guide App</h1>
    <ContentSubmit />
    <FlashCard v-if="flashcards !== null" />
  </div>
</template>

<script>
import ContentSubmit from './components/ContentSubmit.vue'
import FlashCard from './components/FlashCard.vue'

export default {
  name: 'App',
  data() {
    return {
      inputText: "",
      flashcards: null
    }
  },
  components: {
    ContentSubmit,
    FlashCard
  }
}
</script>
