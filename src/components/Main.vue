<template>
    <div class="film">
        <h1>{{info.title}}</h1>
        <h2>{{info.original_title}}</h2>
        <p>{{info.original_language}}</p>
        <p>{{info.vote_average}}</p>
    </div>
</template>

<script>
export default {
    nome:'Main',
    props:['info'],
}
</script>

<style scoped lang="scss">
.film{
    padding:10px;
}
</style>