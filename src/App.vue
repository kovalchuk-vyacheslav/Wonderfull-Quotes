<template>
  <div id="app">
    <div class="container">
      <progress-bar :count="quotes.length" :max-quotes="maxQuotes"></progress-bar>
      <new-quote @add-quote="newQuote"></new-quote>
      <quotes-grid :quotes="quotes"></quotes-grid>
      <div class="alert alert-primary info" role="alert">
        Info: Click on a Quote to delete it
      </div>
    </div>
  </div>
</template>

<script>

    import ProgressBar from "@/components/ProgressBar";
    import QuotesGrid from "@/components/QuotesGrid";
    import NewQuote from "@/components/NewQuote";

    export default {
        name: 'app',
        components: {
            progressBar: ProgressBar,
            quotesGrid: QuotesGrid,
            newQuote: NewQuote
        },
        data() {
            return {
                quotes: [],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote) {
                if (!quote) {
                    return alert("Quote can't be empty");
                }

                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push(quote)
                } else {
                    return alert('No more than 10 quotes are allowed')
                }
            },
        }
    }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Dancing+Script&display=swap');

  .info {
    font-size: 12pt;
    text-align: center;
    margin-top: 30px;
  }
</style>
