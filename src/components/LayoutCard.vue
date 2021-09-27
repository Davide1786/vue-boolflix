<template>
  <section class="cards" >
    <div class="card-front">
        <img v-if="info.poster_path"
        :src="`https://image.tmdb.org/t/p/w300/${info.poster_path}`" alt="" class="image">
        <img v-else
         src="../assets/img/logo.jpg" alt="" class="image">
          <div class="card-retro">         
            <h3>Titolo</h3>
            <p> {{ info.title }} </p>
            <h3>Titolo Originale</h3>
            <p> {{ info.original_title }} </p>
            <h3>Voto</h3>
            <p> {{ info.vote_average }} </p>
            <span>Lingua</span>
            <img v-if="lingue.includes(info.original_language)" 
            class="iconeNazionali"
            :src="require(`../assets/img/bandiera-${info.original_language}.png`)"> 
            <p v-else class="testoLingua">
              non disponibile
            </p>
            <h3>Storia</h3>
            <p> {{ info.overview }} </p>
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
      return Math.ceil(this.info.vote_average)
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

</style>
