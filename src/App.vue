<template>
  <div id="app">
    <HeaderSection @search="search" />
    <MainSection :searchresult="searchresult" />
  </div>
</template>

<script>
import axios from "axios";
import HeaderSection from "./components/HeaderSection.vue";
import MainSection from "./components/MainSection.vue";

export default {
  name: "App",
  components: {
    HeaderSection,
    MainSection,
  },
  data() {
    return {
      searchresult: [],
    };
  },
  created() {
    this.defaultmovies();
  },
  methods: {
    search(moviename) {
      if (moviename != "") {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=50f8b2f6edd169ac26db533d0338821c&query=${moviename}`
          )
          .then((res) => {
            this.searchresult = res.data.results;
          });
      } else {
        this.defaultmovies();
      }
    },
    defaultmovies() {
      axios
        .get(
          `https://api.themoviedb.org/3/trending/movie/week?api_key=50f8b2f6edd169ac26db533d0338821c`
        )
        .then((res) => {
          this.searchresult = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
</style>