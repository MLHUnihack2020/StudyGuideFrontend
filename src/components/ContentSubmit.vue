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

      const jsonBody = {
        text: input
      }

      fetch(endpoint, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(jsonBody),
      })
      .then(response => response.json())
      .then(data => {
        console.log('Success:', data);
      })
      .catch((error) => {
        console.error('Error:', error);
      });
    }
  }
}
</script>
