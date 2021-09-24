<template>
  <div id="app">
    <Header @search="controllo"/>
    <Movies :test="movieSelezionato"/>
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'
import Movies from './components/Movies.vue'

export default {
  name: 'App',
  components: {
    Header,
    Movies
  },
  data() {
    return {
      apiNetflix : 'https://api.themoviedb.org/3/search/movie?api_key=cccfd668f87b751c8d927b2426c90b75&query=',
      movieSelezionato: []
    }
  },
  methods: {
    controllo(filtro) {
      // console.log(filtro);
        axios
            .get(this.apiNetflix + filtro)
            .then(res => {
                // console.log(res.data.results);
                this.movieSelezionato = res.data.results;
            })
    }
  }
}
</script>

<style lang="scss">
@import './style/generals.scss'
</style>
