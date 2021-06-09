<template>
  <main class="container text-center">
    <section class="row gallery">
      <div
        class="col-6 col-sm-4 col-md-3 col-lg-2 album"
        v-for="(album, index) in albums"
        :key="index"
        :class="{ 'offset-lg-1': index % 5 == 0 }"
      >
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
    align-content: flex-start;
    overflow-y: auto;

    .album {
      padding: 10px;
    }
  }

  /*  .gallery {
  display: flex;
  flex-wrap: wrap;
  height: 100%;
  width: 70%;
  margin: 0 auto;
  padding: 20px 0;
  overflow-y: auto;

  .album {
    width: 20%;
    min-width: 155px;
    min-height: 290px;
    height: calc(100% / 2);
    flex-shrink: 0;
    padding: 10px 15px;
    margin: auto;
  }
    } */
}
</style>
