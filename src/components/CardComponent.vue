<template>
    <div class="card">
      <img
          class="card-img-top"
          :src="poster"
          alt="Card image cap"
      >
  
      <div class="card-body">
  
          <h5 class="card-title">
              {{ title }}
          </h5>
  
          <p class="card-text">
              {{ author }}
              <br>
              {{ year }}
          </p>
  
      </div>
  </div>
</template>
  
<script>
    export default {
        props: {
        poster: String,
        title: String,
        author: String,
        year: String,
        }
    }
</script>
  
<style lang="scss" scoped>

    @import '../style/variables.scss';

    .card {
        background-color: $--light;
        padding: 1rem;
        border-radius: 0;
        text-align: center;
        color: grey;
        height: 100%;
        min-height: 360px;

        h5 {
            color: #FFF;
            text-transform: uppercase;
        }

        .card-body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 1rem 0;
        }
    }


</style>