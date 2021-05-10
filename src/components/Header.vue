<template>
    <div class="container">
        <div class="logo">
            <img src="@/assets/boolflix.png" alt="">
        </div>
    
        <div class="form">
            <input type="text" placeholder="Cerca il film o la serie TV." v-model="ricerca">
            <button @click="$emit('performSearch', ricerca)">Invio</button>
        </div>
    </div>
</template>

<script>
export default {
    nome:'Header',
    data(){
        return{
            ricerca:'',
        }
    }
}
</script>

<style scoped lang="scss">
    .container{
        display: flex;
        align-items: center;
        img{
            width: 100px;
        }
    }
</style>