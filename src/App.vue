<template>
  <div id="app">
    <Loader v-if="loading" />
    <Header />
    <Main @loadingData="loadingData" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import Loader from "./components/Loader.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
    Loader,
  },
  data() {
    return {
      loading: true,
    };
  },
  methods: {
    loadingData(boolean) {
      this.loading = boolean;
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
</style>
