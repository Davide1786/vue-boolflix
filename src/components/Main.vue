<template>
  <section class="cards">
    <div v-for="(movie, index) in movies" :key="index" class="card">
       <LayoutCard :info="movie" />
    </div>
  </section>
</template>

<script>
import LayoutCard from './LayoutCard.vue'
export default {
  name: 'Main',
  components: {
    LayoutCard
  },
  data(){
    return {
      title: 'original_title'
    }
  },
  props: ['movies']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.cards {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

// .card {
//   height: 550px;
//   width: 400px;
//   border: 1px solid hotpink;
//   background: cornflowerblue;
//   margin: 60px 60px;
//   text-align: center;
//   // padding: 20px;
//   color: white;
// }

</style>
