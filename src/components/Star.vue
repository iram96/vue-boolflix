<template>
  <div>
    <i
      v-for="(i, index) in this.vote"
      :key="index"
      class="fa-star fa-solid"
    ></i>
  </div>
</template>

<script>
export default {
  name: "Star",
  props: ["vote"],
};
</script>

<style scoped lang='scss'>
i {
  height: 10px;
}
</style>