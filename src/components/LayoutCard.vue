<template>
  <section class="cards">
    <div class="card-front">
        <img v-if="info.poster_path"
        :src="`https://image.tmdb.org/t/p/w300/${info.poster_path}`"
        alt="" class="image">
        <img v-else
         src="../assets/img/logo.png" alt="">
          <div class="card-retro">         
            <h3>Titolo</h3>
            <p> {{ info.title ? info.title : info.name }} </p>
            <h3>Titolo Originale</h3>
            <p> {{ info.original_title ? info.original_title : info.original_name }} </p>
            <h3>Voto</h3>
            <div class="voto">
              <i v-for="n in 5" :key="n" class="fa-star"
              :class="(n <= getVoto()) ? 'fas' : 'far'">   
              </i>
            </div>
            <span>Lingua</span>
            <img v-if="lingue.includes(info.original_language)" 
            class="iconeNazionali"
            :src="require(`../assets/img/bandiera-${info.original_language}.png`)"> 
            <p v-else class="testoLingua">
              non disponibile
            </p>
            <h3>Storia</h3>
            <p> {{ info.overview ? info.overview : 'Storia non disponibile' }} </p>
          </div>
    </div>

  </section>
</template>

<script>

export default {
  name: 'LayoutCard',
  props: ['info'],

  data: function() {
    return {
      lingue: [ 'de', 'es', 'it', 'jp', 'us', 'en']
    }
  },
  methods: {
    getVoto: function() {
      return Math.ceil(this.info.vote_average / 2)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.cards {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.card-front {
  height: 550px;
  width: 400px;
  margin: 10px 10px;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card-retro {
   background: #282828;
   width: 100%;
   height: 100%;
   display: none;
   padding: 30px;
   text-align: center;
   text-align: left;
   overflow: scroll;
}

.image {
  width: 100%;
  height: 100%;
}

.card-front:hover > img {
  display: none;
}

.card-front:hover .card-retro {
  display: block;
}

.iconeNazionali {
  width: 30px;
  height: 20px;
  margin-left: 5px;
  vertical-align: middle;
}

.testoLingua {
  display: inline;
}

h3, p {
  margin: 5px auto;
}

.fas {
  color: rgb(222, 200, 34);
}

.far {
  color: rgb(222, 200, 34);
}

</style>
