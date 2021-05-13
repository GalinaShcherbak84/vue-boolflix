<template>
  <main>
    <section >
      <h1 id="first">Film</h1>
      <div class="contcads">
        <Card v-for="(film, index) in films" :key=index :info="film" />
      </div>
    </section>
    
    <section >
      <h1>Serie</h1>
      <div class="contcads">
         <Card v-for="(serie, index) in series" :key="index +'i'" :info="serie" />
      </div>
    </section>
  </main>
</template>

<script>
import Card from "@/components/Card.vue"
export default {
    nome:'Content',
    props:['series', 'films'],
    components:{
      Card,
    }
}
</script>

<style scoped lang="scss">
main{
text-align: center;
color:white;
padding-top: 80px;
overflow:auto;
  section{
  background: black;
  width: 100vw;
  padding-bottom: 10px;
    h1{
    font-size: 36px;
    background: #d81a27;
    }
    .contcads{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    }
  }
}

</style>