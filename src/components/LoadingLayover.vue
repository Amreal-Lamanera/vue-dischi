<template>
  <div class="layover" ref="layover">
    <img src="../assets/loading.gif" alt="">
  </div>
</template>

<script>

export default {

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.layover {
  background-color: #000;
  z-index: 999;
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;

  img {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 50%;
  }

}

</style>
