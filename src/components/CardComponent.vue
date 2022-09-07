<template>
    <div class="card">
        <div class="card-img-top position-relative">
            <img
                :src="poster"
                alt="Card image cap"
            >

            <div class="btn">
                <font-awesome-icon icon="fa-solid fa-play" />
            </div>
        </div>

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

        &:hover .card-img-top::after {
            content: '';
            position: absolute;
            top: 0;
            bottom: 0;
            right: 0;
            left: 0;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .btn {
            display: none;
        }

        &:hover .btn {
            display: flex;
            justify-content: center;
            align-items: center;
            color: #FFF;
            border: 5px solid #FFF;
            border-radius: 100%;
            position: absolute;
            height: 4rem;
            aspect-ratio: 1/1;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            z-index: 1;
            font-size: 2rem;
        }

        h5 {
            color: #FFF;
            text-transform: uppercase;
        }

        .card-img-top {
            cursor: pointer;

            img {
                width: 100%;
            }
        }

        .card-body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 1rem 0;
        }
    }


</style>