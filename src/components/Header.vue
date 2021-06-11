<template>
  <header class="container-fluid sticky-top ">
    <div class="row align-items-center flex-nowrap px-2">
      <!-- <img :src="logo" alt="Logo" class="img-fluid"> -->
      <!-- <img src="../assets/img/spotify.png" alt="Logo"> -->
      <div class="logo">
        <a href="#"></a>
      </div>
      <!-- <div class="flex-shrink-1 d-flex justify-content-end">
        <FilterSelect
          labelFilter="Genere"
          :options="musicGenre"
          @filterSelect="$emit(filterSelect)"
        />
        <FilterSelect
          class="mx-2"
          labelFilter="Artista"
          :options="filteredArtist"
          :currentOption="currentArtist"
          @filterSelect="$emit(filterSelect)"
        />
      </div> -->
    </div>
  </header>
</template>

<script>
// import FilterSelect from "./FilterSelect.vue";

export default {
  name: "Header",
  components: {
    // FilterSelect,
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/variables.scss";

header {
  height: $header_h;
  background-color: $bg_light;

  .logo {
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
  select {
    max-width: 200px;
  }
}
</style>
