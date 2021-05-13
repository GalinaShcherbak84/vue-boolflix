<template>
  <div id="app">
    <div class="header">
      <Header @performSearch="searchFilm"/> 
    </div>
    <div class="main">
        <Content :series="serie" :films="films"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from "@/components/Header.vue"
import Content from "@/components/Content.vue"

export default {
  name: 'App',
  components: {
    Header,
    Content,
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
      if(text !== ''){
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
}
</script>

<style lang="scss">
@import'@/components/vars/vars.scss';
@import '~@fontsource/roboto/index.css';
@import '~@fontsource/roboto/700.css';
  *{
    margin: 0;
    padding:0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
  }
  #app{
    min-height:100vh;
    background: $mycolor;
    position: relative;
  }
</style>
