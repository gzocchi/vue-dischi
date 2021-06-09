<template>
  <div>
    <img :src="item.poster" alt="item.title" />
    <h3 class="my-3">{{ item.title }}</h3>
    <p>
      {{ item.author }} <br />
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
@import "../style/general";

div {
  height: 100%;
  padding: 10px;
  background-color: $bg_light;

  img {
    width: 100%;
  }

  h3 {
    font-weight: 700;
    font-size: 1.2em;
    text-transform: uppercase;
  }
  p {
    color: rgba($text_color, 0.6);
    line-height: 1.1em;
  }
}
</style>
