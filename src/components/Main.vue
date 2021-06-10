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
    <div class="filter_select sticky-top m-2">
      <AlbumFilter
        class="m-2"
        labelFilter="Genere"
        :options="musicGenre"
        @filter="genreSelected"
      />
      <AlbumFilter
        class="m-2"
        labelFilter="Artista"
        :options="musicArtist"
        @filter="artistSelected"
      />
    </div>
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
      musicArtist: [],
      currentGenre: "",
      currentArtist: "",
    };
  },
  computed: {
    filter() {
      if (this.currentGenre == "" && this.currentArtist == "") {
        return this.albums;
      }
      const newAlbum = this.albums.filter((element) => {
        let genre = element.genre;
        let artist = element.author;
        return (
          genre.includes(this.currentGenre) &&
          artist.includes(this.currentArtist)
        );
      });
      return newAlbum;
    },
  },
  methods: {
    genreSelected(genre) {
      this.currentGenre = genre;
    },
    artistSelected(artist) {
      this.currentArtist = artist;
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
          if (!this.musicArtist.includes(element.author)) {
            this.musicArtist.push(element.author);
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
  .filter_select {
    position: absolute;
    top: $header_h;
    right: 20px;
  }
}
</style>
