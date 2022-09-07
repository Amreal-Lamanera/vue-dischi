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
  
  <style>
  
  </style>