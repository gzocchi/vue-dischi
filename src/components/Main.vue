<template>
  <main class="container p-3 text-center">
    <section class="gallery">
      <div class="album" v-for="(album, index) in albums" :key="index">
        <Album :item="album" />
      </div>
    </section>
  </main>
</template>

<script>
import Album from "./Album.vue";

import axios from "axios";

export default {
  name: "Main",
  components: {
    Album,
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      albums: [],
    };
  },
  created() {
    axios
      .get(this.apiUrl)
      .then((response) => {
        this.albums = response.data.response;
      })
      .catch(function(error) {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scoped>
@import "../style/general";

main {
  height: $main_h;

  .gallery {
    display: flex;
    flex-wrap: wrap;
    height: 100%;
    width: 70%;
    margin: 0 auto;
    padding: 20px 0;

    .album {
      width: 20%;
      max-height: calc(100% / 2);
      flex-shrink: 0;
      padding: 10px 15px;
    }
  }
}
</style>
