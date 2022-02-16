<template>
  <div>
    <i
      v-for="i in 5"
      :key="i"
      class="fa-star"
      :class="i <= vote ? 'fa-solid' : 'fa-regular'"
    ></i>
  </div>
</template>

<script>
export default {
  name: "Star",
  props: ["vote"],
  computed: {},
};
</script>

<style scoped lang='scss'>
i {
  height: 10px;
}
</style>