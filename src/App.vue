<template>
    <div id="main-template">
      <!-- <h1>{{ test }}</h1>
      <h2 @click="booleanTest = !booleanTest">{{ booleanTest }}</h2>
      <button @click="changeAmount('test')">KLIKEJ</button> -->
      <Books />
    </div>
  </template>
  
  <script>
  import Books from './components/Books.vue'
  
  export default {
    data() {
      return {
        booleanTest: true,
        test: 4,
      }
    },
  
    methods: {
      changeAmount(variable, minimum = 3, maximum = 10, changeBy = 2) {
        if (this[variable] >= maximum) {
          this[variable] = minimum;
        } else {
          this[variable] += changeBy;
        }
      }
    },
  
    components: {
      Books
    },
  }
  </script>
  
  <style></style>