<template>
  <div>
    <section>
      <h1>Film</h1>
      <Card v-for="(film, index) in films" :key=index :info="film" />
    </section>
    <section >
      <h1> 0">Serie TV</h1>
      <Card v-for="(serie, index) in series" :key="index +'i'" :info="serie" />
    </section>
  </div>
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

</style>