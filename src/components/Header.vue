<template>
  <div class="header">
    <div class="logo">
      <img src="../assets/img/logo.png" class="logotipo" alt="">
    </div>
      <form>
        <input v-model="ricercaUtente"
               type="text" placeholder="Inserisci il tuo titolo"
                @keyup="$emit('search', ricercaUtente)">        
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
  },
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
  position: sticky;
  top: 0;
  z-index: 9;
  

    .logo {
      width: 50%;
      height: 100%;
      display: flex;
      align-items: center;

        img {
          width: 20%;
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
  }

}

</style>
