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
          <Album :item="album" @filterByAuthor="filterBy" />
        </div>
      </div>
    </section>
    <div class="filter_select sticky-top d-flex ">
      <FilterSelect
        labelFilter="Genere"
        :options="musicGenre"
        @filterSelect="filterBy"
      />
      <FilterSelect
        class="mx-2"
        labelFilter="Artista"
        :options="filteredArtist"
        :currentOption="currentArtist"
        @filterSelect="filterBy"
      />
    </div>
  </main>
</template>

<script>
import Album from "./Album.vue";

import axios from "axios";

// DEBUG
import FilterSelect from "./FilterSelect.vue";

export default {
  name: "Main",
  components: {
    Album,
    FilterSelect,
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
    filteredArtist() {
      const artist = [];
      if (this.currentGenre == "") {
        return this.musicArtist;
      }
      this.albums.forEach((element) => {
        if (
          element.genre == this.currentGenre &&
          !artist.includes(element.author)
        ) {
          artist.push(element.author);
        }
      });
      return artist;
    },
  },
  methods: {
    filterBy(array) {
      switch (array[0]) {
        case "Genere":
          this.currentGenre = array[1];
          this.currentArtist = "";
          break;
        case "Artista":
          this.currentArtist = array[1];
          break;
      }
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
        this.$emit("loadingData", false);
      })
      .catch(function(error) {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/variables.scss";

main {
  height: $main_h;

  .gallery {
    height: 100%;
  }

  // DEBUG
  .filter_select {
    position: absolute;
    top: calc(#{$header_h} / 2);
    transform: translateY(-50%);
    right: 20px;
  }
}
</style>
