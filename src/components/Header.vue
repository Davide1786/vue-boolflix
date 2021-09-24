<template>
  <div class="header">
    <div class="logo">
      <h1 class="logotipo">BOOLFLIX</h1>
    </div>
      <form>
        <input v-model="ricercaUtente"
               type="text" placeholder="Inserisci il tuo titolo">
        <button @click.prevent="$emit('search', ricercaUtente)">Cerca titolo</button>
      </form>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      ricercaUtente: ''
    }
  }
  // props: {
  //   msg: String
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/variablse';

.header {
  width: 100%;
  height: 80px;
  background: $blackbackgroun;
  display: flex;
  justify-content: space-around;
  align-items: center;

    .logo {
      width: 50%;
      height: 100%;
      display: flex;
      align-items: center;
      
        .logotipo {
          color: red;
        }
    }
  input {
    margin-right: 20px;
    padding: 10px;
    border-radius: 3px;
    border: none;
    outline: none;
  } 
  button {
    padding: 10px;
    border-radius: 3px;
    border: none;

    // border-radius: 5px;
    

  }

}

</style>
