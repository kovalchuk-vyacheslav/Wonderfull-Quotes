<template>
  <p @click="$emit('deleteQuote', index)">
    <slot></slot>
  </p>
</template>

<script>
    export default {
        name: "Quote",
        props: [
            'index'
        ]
    }
</script>

<style scoped>
  p {
    display: inline-block;

    font-family: 'Dancing Script', cursive;
    font-style: italic;
    font-weight: bold;

    padding: 10px;
    margin: 15px;

    border-radius: 2px;
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.5);

    width: 300px;
  }

  p:hover {
    background-color: lightcoral;
    cursor: pointer;
  }
</style>