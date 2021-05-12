<template>
    <div class="container">
      <img v-show="info.backdrop_path !== null" class="sfondo" :src="`https://image.tmdb.org/t/p/w500${info.backdrop_path}`" alt="">
      <div class="scuro"></div>

      <div class="inform">
            <div>
                <p>Titolo originale:</p>
                <h3>{{info.original_title?info.original_title:info.original_name}}</h3>
            </div>
            <h1>{{info.title?info.title:info.name}}</h1>
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
            <div class="stelle" v-show="info.vote_average==0">
                <i class="far fa-star" v-for="(n,index) in 5" :key ="index + 'a'" ></i>
            </div>
            <div class="stelle" v-show="Math.ceil(info.vote_average)<2 && Math.ceil(info.vote_average)>0">
                <i class="fas fa-star"></i>
                <i class="far fa-star" v-for="(n,index) in 4" :key ="index + 'b'"></i>
            </div>
            <div class="stelle" v-show="Math.ceil(info.vote_average)<=4 && Math.ceil(info.vote_average)>2">
                <i class="fas fa-star" v-for="(n,index) in 2" :key ="index + 'c'"></i>
                <i class="far fa-star" v-for="(n,index) in 3" :key ="index + 'd'"></i>
            </div>
            <div class="stelle" v-show="Math.ceil(info.vote_average)<=6 && Math.ceil(info.vote_average)>4 ">
                <i class="fas fa-star" v-for="(n,index) in 3" :key ="index + 'e'"></i>
                <i class="far fa-star" v-for="(n,index) in 2" :key ="index + 'f'"></i>
            </div>
            <div class="stelle" v-show="Math.ceil(info.vote_average)<=8 && Math.ceil(info.vote_average)>6">
                <i class="fas fa-star" v-for="(n,index) in 4" :key ="index + 'g'"></i>
                <i class="far fa-star"></i>
            </div>
            <div class="stelle" v-show="Math.ceil(info.vote_average)<=10 && Math.ceil(info.vote_average)>8">
                <i class="fas fa-star" v-for="(n,index) in 5" :key ="index + 'h'"></i>
            </div> 
      </div>
      <div v-show="info.overview !=='' " class="testo">{{info.overview}}</div>
      <div v-show="info.overview ==='' " class="testo"><p>Non ci sono informazioni su questo film.</p></div>
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
    methods:{
            
    } 
}
</script>

<style scoped lang="scss">
.container{
position: relative;
text-align: center;
width: 200px;
height: 320px;
background: darkgray;
color:white;
margin:5px;
    .sfondo{
    width: 200px;
    height: 320px; 
    object-fit: cover;
     object-position: center;
    position: relative; 
    z-index: 2; 
    }
    .scuro{
    width: 200px;
    height: 320px;
     background: rgba($color: #000000, $alpha:0.2); 
    position: absolute;
    top:0px;
    left:0px;
    z-index: 3;
    }
    .inform{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    text-shadow: 2px 2px 5px black;
    position: absolute;
    top:0px;
    left:0px;
    width: 200px;
    height: 320px; 
    z-index: 4;
    padding: 10px;
        
        h1{
            font-size: 32px;
            margin-bottom: 10px;
        }
        h3{
            font-size: 18px;
            margin-bottom: 10px;
        }
        
        .lingua{
        margin-bottom: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
            img{
            width: 30px;
            margin-left: 5px;
            }
        }
        .stelle{
            color:yellow;
        }
    }
    .testo{
        position: absolute;
        top:0px;
        left:0px;
        width: 200px;
        height: 320px; 
        background: black;
        z-index: 5;
        color:white;
        padding: 20px;
        overflow: auto;
        opacity: 0;
        transition: opacity .5s;
    }
    
}
.container:hover .testo{
        opacity: 100%;
    }
</style>