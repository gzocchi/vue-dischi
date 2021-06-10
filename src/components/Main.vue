<template>
  <main class="container-fluid text-center">
    <section class="container align-content-start overflow-auto p-4 gallery">
      <div class="row">
        <div
          class="col-6 col-sm-4 col-md-3 col-lg-2 p-3 album"
          v-for="(album, index) in filter"
          :key="index"
          :class="{ 'offset-lg-1': index % 5 == 0 }"
        >
          <Album :item="album" />
        </div>
      </div>
    </section>
    <AlbumFilter
      class="sticky-top"
      :genres="musicGenre"
      @genreSelected="genreSelected"
    />
  </main>
</template>

<script>
import Album from "./Album.vue";

import axios from "axios";

// DEBUG
import AlbumFilter from "./AlbumFilter.vue";

export default {
  name: "Main",
  components: {
    Album,
    AlbumFilter,
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      albums: [],
      musicGenre: [],
      currentGenre: "",
    };
  },
  computed: {
    filter() {
      if (this.currentGenre == "") {
        return this.albums;
      }
      const newAlbum = this.albums.filter((element) => {
        return element.genre.includes(this.currentGenre);
      });
      return newAlbum;
    },
  },
  methods: {
    genreSelected(genre) {
      console.log(genre);
      this.currentGenre = genre;
    },
  },
  created() {
    axios
      .get(this.apiUrl)
      .then((response) => {
        this.albums = response.data.response;
        this.albums.forEach((element) => {
          if (!this.musicGenre.includes(element.genre)) {
            this.musicGenre.push(element.genre);
          }
        });
        // this.$emit('musicGenre', this.musicGenre);
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

  // DEBUG
  .filter {
    position: absolute;
    top: 5px;
    right: 20px;
  }
}
</style>
