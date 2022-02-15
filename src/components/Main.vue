<template>
  <div>
    <div class="container">
      <section>
        <h4>Movies</h4>
        <Card v-for="movie in movies" :key="movie.id" :item="movie" />
      </section>
      <section>
        <h4>Series</h4>
        <Card v-for="serie in series" :key="serie.id" :item="serie" />
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
};
</script>

<style>
</style>