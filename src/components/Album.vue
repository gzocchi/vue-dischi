<template>
  <div class="p-2">
    <img :src="item.poster" alt="item.title" class="img-fluid" />
    <h3 class="my-2 text-uppercase">{{ item.title }}</h3>
    <p class="m-0" @click="$emit('filterByAuthor', [`Artista`, item.author])">
      {{ item.author }}
    </p>
    <p class="m-0">
      {{ item.year }}
    </p>
  </div>
</template>

<script>
export default {
  name: "Album",
  props: ["item"],
};
</script>

<style lang="scss" scoped>
@import "../assets/style/variables.scss";

div {
  height: 100%;
  background-color: $bg_light;

  h3 {
    font-weight: 700;
    font-size: 1.2em;
  }
  p {
    color: rgba($text_color, 0.6);
    line-height: 1.2em;

    &:first-of-type {
      cursor: pointer;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>
