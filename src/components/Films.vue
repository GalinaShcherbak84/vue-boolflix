<template>
<div class="container">
    <div class="film">
        <h2>{{info.title}}</h2>
        <h3>{{info.original_title}}</h3>
        <p>{{info.original_language}}</p>
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
}
</style>