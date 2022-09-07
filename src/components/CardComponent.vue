<template>
    <div class="card h-100">
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

        img{
            height: 150px;
        }

        h5 {
            color: #FFF;
        }

        .card-body {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
    }


</style>