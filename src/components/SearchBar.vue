<template>
  <div>
    <input type="text" v-model="userSelect" @keyup.enter="emitSearch" />
    <button class="btc btn-light" @click="emitSearch">CERCA</button>
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

<style scoped lang='scss'>
input {
  border-top-left-radius: 20px;
  border-bottom-left-radius: 20px;
  padding-left: 10px;
}
</style>