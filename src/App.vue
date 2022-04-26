<template>
  <div id="app">
    <HeaderSection @search="search" />
    <MainSection
      :moviesearchresult="moviesearchresult"
      :tvsearchresult="tvsearchresult"
    />
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
      moviesearchresult: [],
      tvsearchresult: [],
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
            this.moviesearchresult = res.data.results;
          });
        axios
          .get(
            `https://api.themoviedb.org/3/search/tv?api_key=50f8b2f6edd169ac26db533d0338821c&query=${moviename}`
          )
          .then((res) => {
            this.tvsearchresult = res.data.results;
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
          this.moviesearchresult = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-size: 18px;
  font-family: Arial, Helvetica, sans-serif;
}
body {
  background-color: #141414;
}
::-webkit-scrollbar {
  width: 6px;
}
::-webkit-scrollbar-thumb {
  background-color: #3a3a3a;
}
::-webkit-scrollbar-corner{
  background: none;
}
</style>