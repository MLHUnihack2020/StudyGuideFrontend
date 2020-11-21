<template>
  <div class="m-16 flex" id="app">
    <div>
      <h1 class="text-6xl font-bold">Studyguide Generator</h1>
      <ContentSubmit />
    </div>
    <div>
      <FlashCard v-if="flashcards !== null" />
    </div>
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
