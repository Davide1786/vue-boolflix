<template>
  <div class="cards">
    <div class="card"
    v-for="(movie, index) in movies"
    :key="index" :img="movie.patch_"
    :title="movie.title" :lingua="movie.original_language" >
      <li>
        <!-- {{ movie.title }} 
        {{ movie.original_title }} 
        {{ movie.original_language }} 
        {{ movie.vote_count }}  -->
      </li>
    </div>

    
  </div>
</template>

<script>
// import LayoutCard from './LayoutCard.vue'
export default {
  name: 'Main',
  // components: {
  //   LayoutCard
  // },
  props: ['movies', 'titolo', 'lingua', 'voti', 'img', 'titoloOriginale']
  // data() {
  //   return {
  //     ricercaUtente: ''
  //   }
  // }
  // props: {
  //   msg: String
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

li {
  list-style: none;
}

.cards {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.card {
  height: 550px;
  width: 400px;
  border: 1px solid hotpink;
  background: cornflowerblue;
  margin: 60px 60px;
  text-align: center;
  padding: 20px;
  color: white;
}

</style>
