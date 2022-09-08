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
        <option v-for="genre,i in getGenres" :key="i">
          {{ genre }}
        </option>
      </select>

      <select
        v-model="author"
        @change="$emit('authorChanged', author)"
        class="rounded"
       >
        <option value="">Filtra per Autore</option>
        <option v-for="author,i in getAuthors" :key="i">
          {{ author }}
        </option>
      </select>

    </div>

  </header>
</template>

<script>
  export default {
    props: {
      songs: Array
    },
    data() {
      return {
        genre: '',
        author: ''
      }
    },
    computed: {
      getGenres() {
        const genres = new Array();
        this.songs.forEach(el => {
          genres.push(el.genre);
        });
        const uniq = [...new Set(genres)];
        return uniq;
      },
      getAuthors() {
        const authors = new Array();
        this.songs.forEach(el => {
          authors.push(el.author);
        });
        const uniq = [...new Set(authors)];
        return uniq;
      }
    },
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