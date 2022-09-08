<template>
  <div id="app">
    <HeaderComponent
      @genreChanged="onGenreChange"
      @authorChanged="onAuthorChange"
      :songs="songs"
    />
    <MainComponent
      :filterDataGenre="filterGenre"
      :filterDataAuthor="filterAuthor"
      :loaded="loaded"
      :songs="songs"
     />
    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';
import axios from 'axios';


export default {
    name: 'App',
    components: {
    HeaderComponent,
    MainComponent,
    FooterComponent,
  },
  data() {
      return {
          filterGenre: "",
          filterAuthor: "",
          loaded: false,
          songs: []
      };
  },
  methods: {
      onGenreChange(data) {
        // console.log('CAMBIO GENERE');
          this.filterGenre = data;
      },
      onAuthorChange(data) {
        // console.log('CAMBIO AUTORE');
          this.filterAuthor = data;
      }
  },
  created() {
    axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then(res => {
            // console.log("risposta della api con i data: ", res.data.response);
            this.songs = res.data.response;
        })
        .catch((err) => {
            console.log("Errore: ", err);
        })
        .finally(() => {
            // do un piccolo ritardo per far vedere il caricamento in ogni caso
            setTimeout(() => {
                this.loaded = true
            },1000)
            //TODO: CORREZIONE NOME MJ
            this.songs.forEach((el) => {
                if(el.author === 'Michael Jacjson') el.author = 'Michael Jackson'
            })
        });

  },
}
</script>

<style lang="scss">

// @import "../node_modules/font-awesome/css/font-awesome.css";
// @import "../node_modules/font-awesome/css/font-awesome.min.css";


  * {
    font-family: "Roboto", sans-serif;
  }
  
  #app {
    display: flex;
    flex-direction: column;
    height: 100vh;
  }

</style>
