<template>
  <div class="p-2">
    <img :src="item.poster" alt="item.title" class="img-fluid" />
    <h3 class="my-3 text-uppercase">{{ item.title }}</h3>
    <p class="m-0"
    @click="$emit('filter', item.author)">
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
    line-height: 1.1em;

    &:first-of-type {
      cursor: pointer;
    }
  }
}
</style>
