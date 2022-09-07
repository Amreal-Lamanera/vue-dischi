<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';

export default {
    name: 'App',
    components: {
    HeaderComponent,
    MainComponent
}
}
</script>

<style lang="scss">

  * {
    font-family: "Roboto", sans-serif;
  }

  #app {
    display: flex;
    flex-direction: column;
    height: 100vh;
  }

</style>
