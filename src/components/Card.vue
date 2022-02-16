<template>
  <div class="p-4 position-relative general-card">
    <img :src="getImgPoster" :alt="item.title" class="poster" role="button" />

    <div class="position-absolute top-50 start-50 translate-middle infos">
      <div
        class="position-absolute top-50 start-50 translate-middle text-white"
        role="button"
      >
        <h4 class="font-white">{{ item.title || item.name }}</h4>
        <span class="font-14 text-center d-block my-3">{{
          item.original_title || item.original_name
        }}</span>
        <span class="font-14 text-center d-block my-3">{{
          item.vote_average
        }}</span>
        <div class="star-slot text-warning">
          <Star :vote="getVote" />
        </div>

        <img :src="flagImg" :alt="item.original_language" class="flag-class" />
      </div>
    </div>
  </div>
</template>

<script>
import Star from "./Star.vue";
export default {
  name: "MovieCard",
  components: {
    Star,
  },
  props: ["item"],
  data() {
    return {
      starsList: [],
    };
  },
  computed: {
    flagImg() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    getVote() {
      const vote = Math.ceil(this.item.vote_average / 2);
      return vote;
    },
    getImgPoster() {
      if (!this.item.poster_path) {
        return "https://www.altavod.com/assets/images/poster-placeholder.png";
      }
      return `https://image.tmdb.org/t/p/w342` + this.item.poster_path;
    },
  },
};
</script>

<style scoped lang='scss'>
.general-card {
  .infos {
    opacity: 0;
    height: 100%;
    min-width: 342px;
    background-color: black;
    transition: 0.5s;

    .flag-class {
      width: 30px;
      height: 15px;
    }
  }
}
.general-card:hover .infos {
  opacity: 1;
  z-index: 1;
}
</style>