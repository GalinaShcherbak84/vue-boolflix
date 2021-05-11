<template>
<div class="container">
    <div class="serie">
        <h2>{{info.name}}</h2>
        <h3>{{info.original_name}}</h3>
        <p>{{info.original_language}}</p>
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
}
</style>