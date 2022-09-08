<template>
  <div id="app">
    <HeaderComponent @genreChanged="onGenreChange" @authorChanged="onAuthorChange" />
    <MainComponent :filterDataGenre="filterGenre" :filterDataAuthor="filterAuthor" />
    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';

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
          filterAuthor: ""
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
