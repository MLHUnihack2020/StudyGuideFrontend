<template>
  <div class="hello">
    <p class="text-lg font-bold">{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
