<template>
  <header class="container-fluid">
    <!-- <img :src="logo" alt="Logo" class="img-fluid"> -->
    <!-- <img src="../assets/img/spotify.png" alt="Logo"> -->
    <div>
      <a href="#"></a>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
@import "../style/general";

header {
  height: $header_h;
  background-color: $bg_light;

  div {
    height: $header_h;
    width: $header_h;
    background-image: url(#{$imagePath}/spotify.png);
    background-size: 90%;
    background-position: center;
    background-repeat: no-repeat;
    
    a {
      display: block;
      height: 100%;
    }
  }
  // img {
  //   height: 100%;
  //   padding: 5px;
  // }
}
</style>
