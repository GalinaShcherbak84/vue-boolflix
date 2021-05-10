<template>
  <div id="app">
    <div class="header">
      <Header @performSearch="searchFilm" /> 
    </div>
    <div class="main">
      <Main v-for = "(film, index) in  films" :key ='index' :info ="film"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from "@/components/Header.vue"
import Main from "@/components/Main.vue"
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      films:[],
      urlFilm:'https://api.themoviedb.org/3/search/movie?api_key=257625abe3fa656fc29461483ca0c0aa&query=fantozzi&language=it-IT'
    }
  },
  
  methods:{
    searchFilm(text){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=257625abe3fa656fc29461483ca0c0aa&',
      {
        params:{
          query: text,
          language:'it-IT'
        }
      })
      .then(res=>{
          console.log(res.data.results);
          this.films=res.data.results;
          console.log(this.films)
          
      })
      .catch(err=>{
          console.log('Errore',err);
      })
    }
  }
}
</script>

<style lang="scss">

</style>
