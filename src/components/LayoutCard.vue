<template>

<div class="flip-card">

  <div class="flip-card-inner">

    <div class="flip-card-front">
      <img v-if="info.poster_path"
          :src="`https://image.tmdb.org/t/p/w300/${info.poster_path}`"
          alt="" class="image">
          <img v-else
          src="../assets/img/logo.png" class="logotipo" alt="">
    </div>
    
    <div class="flip-card-back">
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
  
</div>
  

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
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


.flip-card {
  background-color: transparent;
  height: 450px;
  width: 300px;
  perspective: 1000px; 
  margin: 10px 10px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: left;
  transition: transform 0.8s;
  transform-style: preserve-3d;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  // -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

.flip-card-front {
  display: flex;
  justify-content: center;
  align-items: center;  
}

.flip-card-back {
  color: white;
  padding: 30px;
  transform: rotateY(180deg);
  overflow: scroll;
  background: #282828;
}

.image {
  width: 100%;
  height: 100%; 
}

.logotipo {
  width: 100%;
  padding: 10px;
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
