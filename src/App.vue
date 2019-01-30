<template>
  <div id="app">
 
   
     <LandingPage/>
     
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import LandingPage from './components/LandingPage.vue'
import ListFares from './components/ListFares.vue';
export default {
  name: 'app',
  components: {
  
    LandingPage,
    // ListFares
    
  }
}
</script>

<style>
  *{
    margin:0;
    padding:0;
  }
  body{
background-color: #5661a7;
  }
  img{
    max-width: 100%;
    height: auto;
  }
#app {

  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
 

  
}
</style>
