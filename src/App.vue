<template>
  <div id="app">
    <div class="container">
      <progress-bar :count="quotesCount"></progress-bar>
      <div class="quote-input-wrapper">
        <label for="new_quote">Quote</label>
        <textarea name="new_quote" id="new_quote" class="form-control" ref="new_quote_input"></textarea>
        <button class="btn btn-primary" id="add-quote" @click="addQuote">Add quote</button>
      </div>
      <div class="quotes-wrapper" ref="quotes_wrapper">
        <quote v-for="(quoteContent, index) in quotesContent"
               :index="index"
               :key="index"
               @deleteQuote="deleteQuote(index)">
          {{ quoteContent}}
        </quote>
      </div>
      <div class="alert alert-primary info" role="alert">
        Info: Click on a Quote to delete it
      </div>
    </div>
  </div>
</template>

<script>

    import Quote from "@/components/Quote";
    import ProgressBar from "@/components/ProgressBar";

    export default {
        name: 'app',
        components: {
            quote: Quote,
            'progress-bar': ProgressBar
        },
        data() {
            return {
                quotesContent: []
            }
        },
        computed: {
            quotesCount() {
                return this.quotesContent.length
            }
        },
        methods: {
            addQuote() {
                if (!this.$refs.new_quote_input.value) {
                    alert("Quote can't be empty");
                    return;
                }
                if (this.quotesContent.length < 10) {
                    this.quotesContent.push(this.$refs.new_quote_input.value)
                } else {
                    alert('No more than 10 quotes are allowed')
                }
            },
            deleteQuote(index) {
                this.quotesContent.splice(index, 1)
            }
        }
    }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Dancing+Script&display=swap');

  label[for="new_quote"] {
    font-weight: bold;
  }

  .quote-input-wrapper {
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

  .info {
    font-size: 12pt;
    text-align: center;
    margin-top: 30px;
  }
</style>
