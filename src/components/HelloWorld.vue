<template>
  <div class="hello">
    <div class="q-mx-xl">

      <div class="row justify-center">

        <div class="col-11">
          <h3>Quotes Added</h3>
        </div>

        <div class="col-11 bar">
          <div class="bar text-center" style="background-color: lightblue; padding: 5px"
               :style="{width: quotes.length * 10 + '%'}">
            {{ quotes.length }}/10
          </div>
        </div>

        <div class="col-6">
          <q-input
                  v-model="text"
                  filled
                  type="textarea"
                  style="height: 70%; margin-top: 10px"

          />
        </div>
      </div>

      <div class="row justify-center" style="margin-top: -20px">
        <div class="col-3 center">
          <q-btn @click="pushQuote(text)" color="primary" label="Add Quote"/>
        </div>
      </div>

      <app-quote :quote="quotes" :deleteQuote="deleteQuote" ></app-quote>

      <div class="row" style="margin: 0 40px">
        <div class="col-12 bar" style="background-color: lightblue">
          Info: Click on a quote to delete it
        </div>
      </div>

    </div>
  </div>
</template>

<script>

  import quote from './quote.vue'

  export default {
    name: 'HelloWorld',
    components: {
      appQuote: quote
    },

    data() {
      return {
          text: '',
          quotes: ['Just a quote to start with something', 'fajskdfjalkfjla']
      }
    },

    methods: {
        pushQuote(text) {
            if(text.length > 0 && text.trim().length > 0){
                if(this.quotes.length <= 9) {
                    this.quotes.push(text);
                } else {
                    alert('Maximum number of quotes is 10, please delete some!')
                }
            }
        },
        deleteQuote() {
            let index = this.quotes.indexOf(this.text);
            this.quotes.splice(index,1);
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  .bar {
    background-color: rgb(242, 242, 242);
    text-align: center;
    font-weight: bold;
  }
  .center {
    display: flex;
    justify-content: center;
  }

</style>

