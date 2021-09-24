<template>
  <div>
      <li v-for="(item, index) in test" :key="index">
        {{ item.title }} 
        {{ item.original_title }} 
        {{ item.original_language }} 
        {{ item.vote_count }} 
      </li>
  </div>
</template>

<script>
export default {
  name: 'Movies',
  props: ['test']
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

</style>
