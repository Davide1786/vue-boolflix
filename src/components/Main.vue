<template>
  <section class="cards">
      <!-- <div id="cast">
        ciao
      </div> -->
   
    <div class="row">
      <h1>Film</h1>
        <i @click="scroll_left" class="fas fa-chevron-left"></i>
        <div class="wrapper">
            <div v-for="(movie, index) in movies" :key="index">
              <LayoutCard :info="movie" />
            </div>
        </div>
        <i @click="scroll_right" class="fas fa-chevron-right"></i>
    </div>
    
    <div class="row">
      <h1>Serie</h1>
        <i @click="left" class="fas fa-chevron-left"></i>
        <div class="wrapper-uno">
            <div v-for="(serie, index) in series" :key="index">
              <LayoutCard :info="serie" />
            </div>
        </div>
        <i @click="right" class="fas fa-chevron-right"></i>
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
      title: 'original_title',
      cast: false
    }
  },
  methods: {
    scroll_left() {
      let content = document.querySelector(".wrapper");
      content.scrollLeft -= content.scrollWidth * 4 / 6;
    },
    scroll_right() {
      let content = document.querySelector(".wrapper");
      content.scrollLeft += content.scrollWidth * 4 / 6;
    },
    left() {
      let content = document.querySelector(".wrapper-uno");
      content.scrollLeft -= content.scrollWidth * 4 / 6;
    },
    right() {
      let content = document.querySelector(".wrapper-uno");
      content.scrollLeft += content.scrollWidth * 4 / 6;
      // this.$refs.
    },
  },
  props: ['movies', 'series', 'row']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

  .cards {
    width: 100%;
    position: inherit;
    position: relative;
    top: 50%;
    transform: translate(0%, -55%);
    background: #181818;
    padding: 10px;
  }

  h1 {
    color: white;
    margin-left: 15px ;
  }

  .wrapper, 
  .wrapper-uno {
  display: flex;
  flex-wrap: nowrap;
  width: 100%;
  overflow: auto;
  position: relative;
  scroll-behavior: smooth;
  }

  .row, 
  .row-uno {
    position: relative;
    padding: 0px 40px;
  }

//   #cast {
//     position: absolute;
//     top: 50%;
//     left: 50%;
//     transform: translate(-50%, -50%);
//     z-index: 90;
//     width: 1200px;
//     height: 800px;
//     background: olivedrab;
//     // display: none;
// }


  .fas {
    position: absolute;
    font-size: 30px;
    color: red;
  }

  .fa-chevron-left {
    top: 50%;
    left: 0;
    transform: translate(50%, -50%);
    z-index: 1;
    display: none;
  }

  .fa-chevron-right {
    top: 50%;
    right: 0;
    transform: translate(-50%, -50%);
    z-index: 10;
    display: none;
  }

  .row:hover .fa-chevron-left {
    display: block;
  }
 
  .row:hover .fa-chevron-right {
    display: block;
  }



</style>
