<template>
  <div id="app" class="container">
    <Header @search="controllo"/>
    <Main :movies="movieSelezionato" :series="movieSerie" />
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      apiNetflix : 'https://api.themoviedb.org/3/search/',
      apiFilm: '?api_key=cccfd668f87b751c8d927b2426c90b75&query=',
      movieSelezionato: [],
      movieSerie: [],
    }
  },
  created() {
    this.getControllo()
  },
  methods: {
    getControllo() {
      axios
            .get("https://api.themoviedb.org/3/movie/popular?api_key=cccfd668f87b751c8d927b2426c90b75&page=1")
            .then(res => {
                // console.log(res.data.results);
                this.movieSelezionato = res.data.results;
                axios
                  .get("https://api.themoviedb.org/3/tv/popular?api_key=cccfd668f87b751c8d927b2426c90b75&page=")
                  .then(ris => {
                      // console.log(res.data.results);               
                      this.movieSerie = ris.data.results;   
                  })
            })
    },
    controllo(filtro) {
      // console.log(filtro);
        axios
            .get(this.apiNetflix + 'movie' + this.apiFilm + filtro)
            .then(res => {
                // console.log("Film: " + res.data.results);
                this.movieSelezionato = res.data.results;
            })
        axios
            .get(this.apiNetflix + 'tv' + this.apiFilm + filtro)
            .then(res => {
                // console.log("Serie: " + res.data.results);
                this.movieSerie = res.data.results;
            })
    },
  }
}
</script>

<style lang="scss">
@import './style/generals.scss';

.container {
  background: #181818;
  height: 100vh;
}

</style>