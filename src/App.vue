<template>
  <div id="app" class="container">
    <Header @search="controllo"/>
    <Main :movies="movieSelezionato"/>
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
    }
  },
  // created() {
  //   this.getControllo()
  // },
  methods: {
    controllo(filtro) {
      // console.log(filtro);
        axios
            .get(this.apiNetflix + 'movie' + this.apiFilm + filtro)
            .then(res => {
                // console.log(res.data.results);
                this.movieSelezionato = res.data.results;
            })
        axios
            .get(this.apiNetflix + 'tv' + this.apiFilm + filtro)
            .then(res => {
                // console.log(res.data.results);
                this.movieSelezionato = res.data.results;
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
  width: 100%;
  content: "";
  display: table;
  clear: both;
}

</style>