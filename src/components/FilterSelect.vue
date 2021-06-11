<template>
  <select
    class="form-select form-select-sm"
    aria-label=".form-select-sm example"
    v-model="selectedOption"
    @change="$emit('filterSelect', [labelFilter, selectedOption])"
  >
    <option selected value="">{{ labelFilter }}</option>
    <option v-for="(option, index) in options" :key="index" :value="option">
      {{ option }}
    </option>
  </select>
</template>

<script>
export default {
  name: "FilterSelect",
  props: {
    labelFilter: {
      type: String,
      required: true,
    },
    options: {
      type: Array,
      required: true,
    },
    currentOption: {
      type: String,
      required: false,
    },
  },
  data() {
    return {
      selectedOption: "",
    };
  },
  watch: {
    currentOption(val) {
      this.selectedOption = val;
    },
  },
};
</script>

<style lang="scss" scoped>
// @import "../assets/style/general.scss";
</style>
