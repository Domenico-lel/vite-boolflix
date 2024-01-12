<script>
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import { store } from "./store";
export default {
  name: "App",
  components: { AppHeader, AppMain },
  data() {
    return {
      store,
    };
  },
  methods: {
    handleSearchEvent() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "0b1d9ed99a9aca1ff9756c3ae887b688",
            query: this.store.searchText,
            language: "it-IT",
          },
        })
        .then((response) => {
          this.store.movies = response.data.results;
          console.log(response);
          this.store.movies = response.data.results;
        });
    },
  },
  created() { },
};
</script>

<template>
  <AppHeader @performSearch="handleSearchEvent" />
  <AppMain />
</template>

<style lang="scss">
@use "./styles/main.scss" as *;
</style>