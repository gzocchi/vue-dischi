<template>
  <div class="filter d-flex align-items-center">
    <select
      class="form-select"
      aria-label="Default select example"
      v-model="selectedGenre"
    >
      <option @click="$emit('genreSelected', selectedGenre)" selected value="">Genere</option>
      
      <option 
      v-for="(gener, index) in genres"
      :key="index"
      @click="$emit('genreSelected', selectedGenre)" :value="gener">{{ gener }}
      </option>

      <!-- <option @click="$emit('genreSelected', selectedGenre)" value="Rock">Rock</option>
      <option @click="$emit('genreSelected', selectedGenre)" value="Pop">Pop</option>
      <option @click="$emit('genreSelected', selectedGenre)" value="Jazz">Jazz</option>
      <option @click="$emit('genreSelected', selectedGenre)" value="Metal">Metal</option> -->
    </select>
  </div>
</template>

<script>
export default {
  name: "AlbumFilter",
  props: [ "genres" ],
  data() {
    return {
      selectedGenre: "",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../style/general";
</style>
