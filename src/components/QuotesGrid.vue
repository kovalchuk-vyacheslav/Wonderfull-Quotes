<template>
  <div>
    <quote v-for="(quote, index) in quotes"
           :index="index"
           :key="index"
           @deleteQuote="deleteQuote(index)">
      {{ quote }}
    </quote>
  </div>
</template>

<script>
    import Quote from "@/components/Quote";

    export default {
        name: "QuotesGrid",
        components: {
            'quote': Quote
        },
        props: ['quotes'],
        methods: {
            deleteQuote(index) {
                this.quotes.splice(index, 1)
            }
        }
    }
</script>

<style scoped>

</style>