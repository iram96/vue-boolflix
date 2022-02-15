<template>
  <div>
    <div>
      <div class="bgc-darkgray p-4">
        <img :src="getPoster" :alt="item.title" />

        <h4 class="font-white">{{ item.title || item.name }}</h4>
        <span class="font-14 text-center d-block my-3">{{
          item.original_title || item.original_name
        }}</span>
        <span class="font-14 text-center d-block my-3">{{
          item.vote_average
        }}</span>

        <img :src="flagImg" :alt="item.original_language" class="flag-class" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  props: ["item"],
  data() {
    return {};
  },
  computed: {
    flagImg() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    getPoster() {
      return `https://image.tmdb.org/t/p/w342` + this.item.poster_path;
    },
  },
};
</script>

<style scoped lang='scss'>
.flag-class {
  width: 30px;
  height: 15px;
}
</style>