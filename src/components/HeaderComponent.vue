<template>
  <header class="d-flex justify-content-between">

    <img src="../assets/lama.png" alt="">

    <div class="filters">

      <select
        name="genreSelect"
        v-model="genre"
        @change="$emit('genreChanged', genre)"
        class="rounded me-3"
        @focusin="openGen = true, focusGen = true"
        @focusout="openGen = false, focusGen = false"
        @click="clickHandlerGen"
      >
      
          <option value="" default>{{ !openGen? defGen : '' }}Tutti</option>
  
          <option v-for="genre,i in getGenres" :key="i" :value="genre">
            {{ `${!openGen? defGen : ''} ${genre}` }}
          </option>
        </select>
  
        <select
          name="authorSelect"
          v-model="author"
          @change="$emit('authorChanged', author)"
          class="rounded"
          @focusin="openAut = true, focusAut = true"
          @focusout="openAut = false, focusAut = false"
          @click="clickHandlerAut"
         >
  
          <option value="">{{ !openAut? defAut : '' }}Tutti</option>
  
          <option v-for="author,i in getAuthors" :key="i" :value="author">
            {{ `${!openAut? defAut : ''} ${author}` }}
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
        author: '',
        defGen: 'Genere: ',
        defAut: 'Autore: ',
        openGen: false,
        openAut: false,
        focusGen: false,
        focusAut: false
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
    methods: {

      clickHandlerGen(){
        if(!this.focusGen){
         this.openGen=!this.openGen;
        }
        else this.focusGen = false;
      },
      clickHandlerAut(){
        if(!this.focusAut){
         this.openAut=!this.openAut;
        }
        else this.focusAut = false;
      },

    }

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
          width: 200px;
        }
    }



</style>