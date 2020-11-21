<template>
  <div class="flex h-screen">
    <div class="shadow-lg p-5 rounded-lg w-auto h-64 w-24 m-auto mx-10">
      <div>
        <p v-if="cardSide == 0">{{ this.$parent.flashcards[cardNumber].question }}</p>
        <p v-if="cardSide == 1">{{ this.$parent.flashcards[cardNumber].answer }}</p>
      </div>
      <div>
        <button class="p-5" v-on:click="previous">Previous</button>
        <button class="p-5" v-on:click="flip">Flip</button>
        <button class="p-5" v-on:click="next">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FlashCard',
  data() {
    return {
      cardText: "",
      cardNumber: 0,
      cardSide: 0
    }
  },
  methods: {
    flip: function () {
      this.cardText = "ye";
      if (this.cardSide == 0) {
        this.cardSide = 1;
      } else {
        this.cardSide = 0;
      }
    },
    next: function () {
      this.cardNumber++;
    },
    previous: function () {
      this.cardNumber--;
    }
  }
}
</script>
