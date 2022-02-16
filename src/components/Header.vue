<template>
  <div class="row justify-content-between py-4 header-style">
    <div class="col-4">
      <h1>BOOLFIX</h1>
    </div>
    <SearchBar @search="passSearch" class="col-3" />
  </div>
</template>

<script>
import SearchBar from "./SearchBar.vue";

export default {
  name: "Header",
  data() {
    return {
      searchedName: "",
    };
  },
  components: {
    SearchBar,
  },

  methods: {
    userSearchReassign(choice) {
      this.searchedName = choice;
    },
    passSearch(userSelect) {
      this.userSearchReassign(userSelect);
      this.$emit("pass-search", this.searchedName);
    },
  },
};
</script>

<style scoped lang='scss'>
.header-style {
  background-color: rgb(49, 46, 46);
  border-bottom: 2px black solid;
  h1 {
    color: red;
    font-weight: 900;
    -webkit-text-stroke: 2.5px black;
  }
}
</style>