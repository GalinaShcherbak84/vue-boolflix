<template>
    <div class="container">
      <img :src="`https://image.tmdb.org/t/p/w300${info.backdrop_path}`" alt="">
      <h2>{{info.title?info.title:info.name}}</h2>
      <h3>{{info.original_title?info.original_title:info.original_name}}</h3>
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
    padding:10px;
    .lingua{
        display: flex;
        align-items: center;
        img{
        width: 50px;
        margin-left: 5px;
    }
    }
}
</style>