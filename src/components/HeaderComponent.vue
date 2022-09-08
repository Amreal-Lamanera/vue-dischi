<template>
  <header class="d-flex justify-content-between">

    <img src="../assets/lama.png" alt="">

    <div class="filters">

      <select
        v-model="genre"
        @change="$emit('genreChanged', genre)"
        class="rounded me-3"
       >
        <option value="">Filtra per Genere</option>
        <option>Rock</option>
        <option>Pop</option>
        <option>Jazz</option>
        <option>Metal</option>
      </select>

      <select
        v-model="author"
        @change="$emit('authorChanged', author)"
        class="rounded"
       >
        <option value="">Filtra per Autore</option>
        <option>Bon Jovi</option>
        <option>Queen</option>
        <option>Sting</option>
        <option>Steve Gadd Band</option>
        <option>Iron Maiden</option>
        <option>Eric Clapton</option>
        <option>Deep Purple</option>
        <option>Metallica</option>
        <option>Dave Weckl</option>
        <option>Michael Jackson</option>
      </select>

    </div>

  </header>
</template>

<script>
  export default {
    data() {
      return {
        genre: '',
        author: ''
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

        select {
          background-color: $--dark;
          color: #FFF;
          padding: 0.5rem;

        }
    }



</style>