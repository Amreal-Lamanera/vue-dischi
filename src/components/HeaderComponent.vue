<template>
  <header class="d-flex justify-content-between">

    <img src="../assets/lama.png" alt="">

    <select
      v-model="genre"
      @change="$emit('genreChanged', genre)"
      class="rounded"
     >
      <option value="">Filtra per Genere</option>
      <option>Rock</option>
      <option>Pop</option>
      <option>Jazz</option>
      <option>Metal</option>
    </select>

  </header>
</template>

<script>
  export default {
    data() {
      return {
        genre: ''
      }
    },
    // methods: {
    //   boh() {
    //     console.log(this.genre);
    //   }
    // },
  }
</script>

<style lang="scss" scoped>

    @import '../style/variables.scss';
    
    header {
        // height: 10vh;
        padding: 1rem;
        background-color: $--light;
        
        img {
            height: 50px;
        }
    }



</style>