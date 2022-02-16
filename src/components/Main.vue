<template>
  <div class="main-style pt-4">
    <div class="container">
      <section class="row position-relative">
        <h4
          :class="
            !movies.length
              ? 'd-none'
              : 'position-absolute top-0 start-0 translate-middle section-title-style'
          "
        >
          Movies
        </h4>
        <Card
          v-for="movie in movies"
          :key="movie.id"
          :item="movie"
          class="col-4 p-3"
        />
      </section>
      <section class="row position-relative">
        <h4
          :class="
            !series.length
              ? 'd-none'
              : 'position-absolute top-0 start-0 translate-middle section-title-style'
          "
        >
          Series
        </h4>
        <Card
          v-for="serie in series"
          :key="serie.id"
          :item="serie"
          class="col-4 p-3"
        />
      </section>
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "Main",
  components: {
    Card,
  },
  props: ["movies", "series"],
  methods: {},
};
</script>

<style scoped lang='scss'>
.main-style {
  border-bottom: 3px white;
  background-color: rgb(29, 27, 27);
  .section-title-style {
    color: rgb(177, 13, 13);
    font-weight: 700;
    text-shadow: -10px 5px 5px black;
  }
}
</style>