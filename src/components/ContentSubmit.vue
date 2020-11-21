<template>
  <div class="">
    <p>Paste in your text that you want to study below:</p>

    <textarea id="inputText" name="inputText" v-model="$parent.inputText"></textarea>
    <button v-on:click="sendRequest">Submit</button>
  </div>
</template>

<script>
export default {
  name: 'ContentSubmit',
  methods: {
    sendRequest: function () {
      const input = this.$parent.inputText;

      const endpoint = "https://studyguide-backend-nwitjszpka-ue.a.run.app/";
      // const endpoint = "http://localhost:8080/";

      const jsonBody = { text: input };
      const stringed = JSON.stringify(jsonBody);

      fetch(endpoint, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: stringed,
      })
      .then(response => response.json())
      .then(data => {
        console.log('Success:', data);
        this.$parent.flashcards = data.flashcards
      })
      .catch((error) => {
        console.error('Error:', error);
      });
    }
  }
}
</script>
