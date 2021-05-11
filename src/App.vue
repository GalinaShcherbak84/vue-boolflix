<template>
  <div id="app">
    <div class="header">
      <Header @performSearch="searchFilm"/> 
    </div>
    <div class="main">
      <h1>Film</h1>
      <Films v-for = "(film, index) in  films" :key ='index' :info ="film"/>
      <h1>Serie TV</h1>
      <Serie v-for = "(item, indice) in  serie" :key ="indice+'i'" :info ="item"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from "@/components/Header.vue"
import Films from "@/components/Films.vue"
import Serie from "@/components/Serie.vue"
export default {
  name: 'App',
  components: {
    Header,
    Films,
    Serie
  },
  data(){
    return{
      serie:[],
      films:[],
      urlFilm:'https://api.themoviedb.org/3/search/movie?api_key=257625abe3fa656fc29461483ca0c0aa&query=fantozzi&language=it-IT',
      urlSerie:'https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT&query=scrubs'

    }
  },
  
  methods:{
    searchFilm(text){
      /* //cerca film
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
          //console.log(this.films)
          
      })
      .catch(err=>{
          console.log('Errore',err);
      })
      
    },
    //cerca serie
    searchSerie(text){ 
        axios.get('https://api.themoviedb.org/3/search/tv?api_key=257625abe3fa656fc29461483ca0c0aa&',
      {
        params:{
          query: text,
          language:'it-IT'
        }
      })
      .then(res=>{
          console.log(res.data.results);
          this.serie=res.data.results;
          //console.log(this.serie)
          
      })
      .catch(err=>{
          console.log('Errore',err);
      })  */
       Promise.all([
        axios.get('https://api.themoviedb.org/3/search/tv?api_key=257625abe3fa656fc29461483ca0c0aa&',
        {
          params:{
            query: text,
            language:'it-IT'
          }
        }),
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=257625abe3fa656fc29461483ca0c0aa&',
        {
          params:{
            query: text,
            language:'it-IT'
          }
        })
      ]).then(([serie, film])=>{
          console.log('film', film.data.results);
          console.log('serie',serie.data.results)
          this.serie=serie.data.results;
          this.films=film.data.results;
          
          
      }).catch(err=>{
          console.log('Errore',err);
      })  
    }
  }
}
</script>

<style lang="scss">

</style>
