<template>
  <div id="app">
    <HeaderComponent @genreChanged="onChange" />
    <MainComponent :filterData="filterVar" />
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
          filterVar: ""
      };
  },
  methods: {
      onChange(data) {
          this.filterVar = data;
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
