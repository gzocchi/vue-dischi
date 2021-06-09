<template>
  <header class="container-fluid">
    <!-- <img :src="logo" alt="Logo"> -->
    <img src="../assets/img/spotify.png" alt="Logo">
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
      return {
        //   logo: "../assets/img/spotify.png",
      }
  },
};
</script>

<style lang="scss" scoped>
@import "../style/general";

header {
  height: $header_h;
  background-color: $bg_light;

  img{
      height: 100%;
      padding: 5px;
  }
}
</style>