<template>
  <div class="filter d-flex align-items-center">
    <select
      class="form-select form-select-sm"
      aria-label=".form-select-sm example"
      v-model="filterSelection"
      @change="$emit('filter', filterSelection)"
    >
      <option selected value="">{{ labelFilter }}</option>
      <option v-for="(option, index) in options" :key="index" :value="option"
        >{{ option }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "AlbumFilter",
  props: ["labelFilter", "options"],
  data() {
    return {
      filterSelection: "",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../style/general";
</style>
