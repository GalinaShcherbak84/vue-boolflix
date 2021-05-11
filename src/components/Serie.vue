<template>
<div class="container">
    <div class="img">
        <img :src="`https://image.tmdb.org/t/p/w300${info.backdrop_path}`" alt="">
    </div>
    <div class="serie">
        <h2>{{info.name}}</h2>
        <h3>{{info.original_name}}</h3>
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
        <!-- <p>Voto:{{info.vote_average}}</p> -->
        <div class="stelle" v-show="Math.ceil(info.vote_average)<=2">
            <i class="fas fa-star"></i>
            <i class="far fa-star"></i>
            <i class="far fa-star"></i>
            <i class="far fa-star"></i>
            <i class="far fa-star"></i>
        </div>
        <div class="stelle" v-show="Math.ceil(info.vote_average)<=4 && Math.ceil(info.vote_average)>2">
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="far fa-star"></i>
            <i class="far fa-star"></i>
            <i class="far fa-star"></i>
        </div>
        <div class="stelle" v-show="Math.ceil(info.vote_average)<=6 && Math.ceil(info.vote_average)>4 ">
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="far fa-star"></i>
            <i class="far fa-star"></i>
        </div>
        <div class="stelle" v-show="Math.ceil(info.vote_average)<=8 && Math.ceil(info.vote_average)>6">
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="far fa-star"></i>
        </div>
        <div class="stelle" v-show="Math.ceil(info.vote_average)<=10 && Math.ceil(info.vote_average)>8">
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
        </div> 
        
    </div> 
</div>
</template>

<script>
export default {
    nome:'Serie',
    props:['info'],
}
</script>

<style scoped lang="scss">
.serie{
    padding:10px;
    img{
        width: 50px;
        margin-left: 5px;
    }
    .lingua{
        display: flex;
        align-items: center;
    }
    
}
</style>