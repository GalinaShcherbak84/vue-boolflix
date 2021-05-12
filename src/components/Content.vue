<template>
  <div>
    <section >
      <Card v-for="(film, index) in films" :key=index :info="film" />
    </section>
    <section >
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