<template>
    <!-- una card -->
    <!-- poster -->
    <div class="container">
      <img v-show="info.backdrop_path !== null" class="sfondo" :src="`https://image.tmdb.org/t/p/w500${info.backdrop_path}`" alt="">
      <div class="scuro"></div>
        <!-- informazioni -->
        <div class="inform">
            <div>
                <p>Titolo originale:</p>
                <h3>{{info.original_title?info.original_title:info.original_name}}</h3>
            </div>
            <h1>{{info.title?info.title:info.name}}</h1>
            <!-- lingua -->
            <div class="lingua" v-show="info.original_language !=='it'&& info.original_language !=='en'">
                <p>Lingua originale:</p>
                <p>{{info.original_language}}</p>
            </div>
            <div class="lingua" v-show="info.original_language ==='en'">
                <p>Lingua originale:</p>
                <img src="@/assets/en.png" alt="">
            </div>
            <div class="lingua" v-show="info.original_language ==='it'">
                <p>Lingua originale:</p>
                <img src="@/assets/it.png" alt="">
            </div>
            <!-- stelle -->
            <div class="stelle">
                <i class="fas fa-star" v-for="n in getStars(info.vote_average)" :key="`full-${n}`"></i>
                <i class="far fa-star" v-for="n in 5-getStars(info.vote_average)" :key="`empty-${n}`"></i>
            </div>
        </div>
        <!-- trama dei film e delle serie -->
        <div v-show="info.overview !=='' " class="testo"> 
          <p>{{info.overview}}</p>
          <button>Guardare</button>
        </div>
        <!-- trama assente -->
        <div v-show="info.overview ==='' " class="testo1">
          <p>Non ci sono informazioni su questo film.</p>
          <button>Guardare</button>
        </div>
    </div>
</template>

<script>
export default {
    nome:'Card',
    props:['info'],
    data(){
        return{
           
        }
    },
    /* voto da 1 a 5 */
    methods:{
       getStars(voto){
           return Math.ceil(voto/2);
       }     
    } 
}
</script>

<style scoped lang="scss">
@import'@/components/vars/vars.scss';
.container{
position: relative;
text-align: center;
width: 160px;
height: 300px;
background: $mycolorGrey;
color:white;
margin:20px 10px;
    /* img sfondo */
    .sfondo{
    width: 160px;
    height: 300px; 
    object-fit: cover;
     object-position: center;
    position: relative; 
    z-index: 2; 
    }
    /* tendina scura */
    .scuro{
    width: 160px;
    height: 300px;
    background: rgba($color: $mycolor, $alpha:0.4); 
    position: absolute;
    top:0px;
    left:0px;
    z-index: 3;
    }
    /* informazioni */
    .inform{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    text-shadow: 2px 2px 5px black;
    position: absolute;
    top:0px;
    left:0px;
    width: 160px;
    height: 300px; 
    z-index: 4;
    padding: 10px;
        
        h1{
            font-size: 18px;
           
        }
        h3{
            font-size: 16px;
            
        }
        p{
            font-size: 14px;
        }
        /* lingua */
        .lingua{
            display: flex;
            justify-content: center;
            p{
              font-size: 12px; 
              margin-right: 4px;
            }
            img{
            width: 30px;
            }
        }
        /* stelline */
        .stelle{
            color:$mycolorYellow;
            font-size: 14px;
            i{
                padding:0 2px;
            }
        }
    }
    /* trama */
    .testo,
    .testo1{
        position: absolute;
        top:0px;
        left:0px;
        width: 160px;
        height: 300px; 
        background: $mycolor;
        z-index: 5;
        color:white;
        overflow: auto;
        opacity: 0;
        transition: opacity .5s;
            button{
                background: $mycolorRed;
                border: none;
                padding:5px;
                border-radius: 5px;
                margin-top:10px;
                color:white;
                font-weight: 700px;
                cursor: pointer;
            }
    }
    /* senza trama */
    .testo1{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    
}
.container:hover .testo,
.container:hover .testo1{
        opacity: 100%;
    }
</style>