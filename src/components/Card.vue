<template>
  <div>
    <div>
      <div class="bgc-darkgray p-4">
        <img
          :src="`https://image.tmdb.org/t/p/w342` + this.item.poster_path"
          :alt="item.title"
        />

        <h4 class="font-white">{{ item.title || item.name }}</h4>
        <span class="font-14 text-center d-block my-3">{{
          item.original_title || item.original_name
        }}</span>
        <span class="font-14 text-center d-block my-3">{{
          item.vote_average
        }}</span>
        <div class="star-slot">
          <Star :vote="item.vote_average" />
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
    getStars() {
      let arraylist = this.starsList;
      const stars = Math.ceil(this.item.vote_average / 2);
      console.log(stars);
      if (stars < 2) {
        arraylist.push("star");
      } else if (stars < 3) {
        arraylist.push("star");
      } else if (stars < 4) {
        arraylist.push("star");
      } else if (stars <= 5) {
        arraylist.push("star");
      }
      console.log(arraylist);
      return arraylist;
    },
  },
  mounted() {
    this.getStars();
  },
};
</script>

<style scoped lang='scss'>
.flag-class {
  width: 30px;
  height: 15px;
}
</style>