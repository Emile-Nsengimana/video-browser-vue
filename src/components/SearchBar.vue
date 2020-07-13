<template>
  <div class="search-box">
    <input class="inp-txt" @input="onInput" />
    <button class="btn" @click="onSearch">Search</button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(event) {
      this.$emit("termChange", event.target.value);
    },
    onSearch() {
      this.$emit("search");
    }
  }
};
</script>

<style scoped>
.search-box {
  width: 50%;
  margin: auto;
}
.inp-txt {
  width: 80%;
  line-height: 2.5rem;
  outline: none;
  box-shadow: 0 0 0.5rem 0 rgba(1, 59, 61, 0.5);
  border-radius: 5px;
  border-top: none;
  padding: 0 1rem;
  margin: 2rem 1rem;
}

.btn {
  height: 2.5rem;
  outline: none;
  background-color: rgb(7, 42, 71);
  color: whitesmoke;
  border-radius: 7px;
  border: none;
}

.btn:hover {
  background-color: whitesmoke;
  color: rgb(7, 42, 71);
  border: 0.5px solid rgb(7, 42, 71);
}
</style>
