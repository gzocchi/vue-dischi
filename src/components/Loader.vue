<template>
  <div class="container-fluid loader">
    <img src="../assets/img/spotify.png" alt="Logo" />
  </div>
</template>

<script>
export default {
  name: "Loader",
};
</script>

<style lang="scss" scoped>
@import "../assets/style/variables.scss";

.loader {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1021;
  display: flex;
  justify-content: center;
  align-items: center;
  height: $app_h;
  background-image: radial-gradient($bg_light, $bg_dark 40%);

  img {
    width: $header_h;
    margin: 20px 0;
    animation: logoScale 1s linear infinite alternate;
  }
}
@keyframes logoScale {
  from {
    transform: scale(1);
  }
  to {
    transform: scale(2);
  }
}
</style>
