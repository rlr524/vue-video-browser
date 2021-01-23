<template>
  <div id="searchbar">
    <input @input="onInput" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(e) {
      this.$emit("searchTermChange", e.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 1.25em;
}
</style>