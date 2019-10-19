<template>
  <div class="wrapper">
    <label for="new_quote">Quote</label>
    <textarea name="new_quote" id="new_quote" class="form-control" v-model="quote"></textarea>
    <button class="btn btn-primary" id="add-quote" @click="newQuote">Add quote</button>
  </div>
</template>

<script>
    export default {
        name: "NewQuote",
        data() {
            return {
                'quote': ''
            }
        },
        methods: {
            newQuote() {
                this.$emit('add-quote', this.quote)
                this.quote = ''
            }
        }
    }
</script>

<style scoped>
  label[for="new_quote"] {
    font-weight: bold;
  }

  .wrapper {
    width: 70%;
    margin: 0 auto;
  }

  #add-quote {
    display: block;
    margin: 10px auto;
  }

  #add-quote:focus {
    box-shadow: none;
  }
</style>