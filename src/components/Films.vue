<template>
<div class="container">
    <div class="film">
        <h2>{{info.title}}</h2>
        <h3>{{info.original_title}}</h3>
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
    nome:'Films',
    props:['info'],
}
</script>

<style scoped lang="scss">
.film{
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