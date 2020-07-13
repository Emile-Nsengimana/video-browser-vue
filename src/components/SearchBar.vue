<template>
  <div class="search-box">
    <input class="inp-txt" placeholder="search..." @input="onInput" />
    <div class="btn-group">
      <button class="btn" @click="onSearch">Search</button>
    </div>
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
  width: 100%;
  margin: 2rem auto;
  display: flex;
}
.btn-group {
  margin-left: 10px;
}
.inp-txt {
  flex: 1;
  line-height: 2.5rem;
  outline: none;
  box-shadow: 0 0 0.5rem 0 rgba(1, 59, 61, 0.5);
  border-radius: 5px;
  border-top: none;
  padding: 0 1rem;
}

.btn {
  height: 2.5rem;
  outline: none;
  background-color: #072a47;
  color: whitesmoke;
  border-radius: 7px;
  border: none;
}

.btn:hover {
  background-color: whitesmoke;
  color: rgb(7, 42, 71);
  border: 0.5px solid rgb(7, 42, 71);
}

@media (min-width: 900px) {
  .search-box {
    width: 80%;
  }
}
</style>
