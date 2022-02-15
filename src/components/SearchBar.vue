<template>
  <div>
    <input type="text" v-model="userSelect" @keyup.enter="emitSearch" />
    <button class="btc"></button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      userSelect: "",
    };
  },
  methods: {
    emitSearch() {
      this.$emit("search", this.userSelect);
    },
  },
};
</script>

<style>
</style>