<template>
  <div>
    <SearchBar @search="passSearch" />
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

<style>
</style>