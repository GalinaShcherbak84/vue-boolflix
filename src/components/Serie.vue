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
        <p>{{info.vote_average}}</p>
        
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