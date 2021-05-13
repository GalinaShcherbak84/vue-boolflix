<template>
    <div class="cont">
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
@import'@/components/vars/vars.scss';
    .cont{
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: $mycolorGrey;
        padding:0 30px;
        position: fixed;
        top:0;
        left:0;
        width: 100%;
        height: 80px;
        z-index: 6;
        img{
            width: 100px;
        }
        .form{
            display: flex;
            align-items: center;
            input{
            border:none;
            padding:5px 10px;
            border-radius: 5px;
            width: 240px;
            margin-right: 10px;
            outline: none;
            }
            button{
            background: $mycolorRed;
            border: none;
            padding:5px 10px;
            border-radius: 5px;
            color:white;
            font-weight: 700px;
            cursor: pointer;
            }
        }
        
    }
</style>