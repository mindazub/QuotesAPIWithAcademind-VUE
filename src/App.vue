<template>

      <div id="app">
        <div class="container">
          <div class="row">
            <div class="col-xs-12">
              <router-link to="/">Quotes</router-link>&nbsp&nbsp|&nbsp&nbsp
              <router-link to="/new-quote">New Quote</router-link>&nbsp&nbsp|&nbsp&nbsp
              <router-link to="/signup">Signup</router-link>
            </div>            
          </div>
          <hr>
          <div class="row">
            <div class="col-xs-12">
                <router-view></router-view>
            </div>            
          </div>
        </div>
      </div>
    
</template>

<script>

import NewQuote from './components/new-quote.vue';


  export default {
    data() {
      return {}
    },
    components: {
      'app-new-quote': NewQuote
    }
  }
</script>
  


<style>

#app {
  margin: 25px;
}
  
</style>
