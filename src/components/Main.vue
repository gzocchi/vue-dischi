<template>
  <main class="container-fluid text-center">
    <section class="container align-content-start overflow-auto p-4 gallery">
      <div class="row">
        <div
          class="col-6 col-sm-4 col-md-3 col-lg-2 p-3 album"
          v-for="(album, index) in albums"
          :key="index"
          :class="{ 'offset-lg-1': index % 5 == 0 }"
        >
          <Album :item="album" />
        </div>
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
    // align-content: flex-start;
    // overflow-y: auto;
    height: 100%;

    // .album {
    //   padding: 10px;
    // }
  }
}
</style>
