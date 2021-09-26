<template>
  <section class="cards" >
    <div class="card">
      <img :src="`https://image.tmdb.org/t/p/w300${info.poster_path}`" alt="" class="image">
      <!-- <div class="informazioniGenerali"> -->
          <li class="informazioniGenerali">         
            <p> Titolo: {{ info.title }} </p>
            <p> Titolo Originale: {{ info.original_title }} </p>
            <p> Voto: {{ info.vote_count }} </p>
            <p> Storia: {{ info.overview }} </p> 
          </li>
      <!-- </div> -->
    </div>
  </section>
</template>

<script>
export default {
  name: 'LayoutCard',
  props: ['info']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">



.image {
  width: 100%;
  height: 100%;
}

.cards {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;

    .card {
      height: 550px;
      width: 400px;
      // border: 1px solid hotpink;
      // background: red;
      margin: 10px 10px;
      // padding: 40px;
      text-align: center;
      color: white;
    }

}

// .informazioniGenerali {
//   display: none;
//     li {
//       list-style: none;
//     }
// }

li {
  list-style: none;
  text-align: left;
  padding: 50px;
}

.informazioniGenerali {
  //  background: olive;
  background: #282828;
   widows: 100%;
   height: 100%;
   display: none;
}

.card:hover img {
  display: none;
}

.card:hover .informazioniGenerali {
  display: block;
}






</style>
