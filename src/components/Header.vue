<template>
  <header class="container-fluid sticky-top ">
    <div class="row align-items-center flex-nowrap px-2">
      <!-- <img :src="logo" alt="Logo" class="img-fluid"> -->
      <!-- <img src="../assets/img/spotify.png" alt="Logo"> -->
      <div class="logo">
        <a href="#"></a>
      </div>
      <div class="flex-shrink-1 d-flex flex-row-reverse">
        <!-- <AlbumFilter /> -->
      </div>
    </div>
  </header>
</template>

<script>

export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
@import "../assets/style/variables.scss";

header {
  height: $header_h;
  background-color: $bg_light;

  div.logo {
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
