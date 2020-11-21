<template>
  <div id="app">
    <h1 class="text-5xl font-bold">Study Guide App</h1>
    <ContentSubmit />
    <FlashCard />
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
      flashcards: {
        "0": {
          question: "this is a test 1",
          answer: "answer 1"
        },
        "1": {
          question: "this is a test 2",
          answer: "answer 2"
        },
      }
    }
  },
  components: {
    ContentSubmit,
    FlashCard
  }
}
</script>
