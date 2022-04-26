<template>
  <main>
    <div id="container">
      <MovieCard
        v-for="(elm, i) in moviesearchresult"
        :key="i"
        :moviesearchresult="moviesearchresult"
        :elm="elm"
      />
      <TvCard
        v-for="(elm, i) in tvsearchresult"
        :key="i"
        :tvsearchresult="tvsearchresult"
        :elm="elm"
      />
      <h1
        class="no-results"
        v-show="moviesearchresult.length == 0 && moviesearchresult.length == 0"
      >
        Nessun risultato trovato
      </h1>
    </div>
  </main>
</template>

<script>
import MovieCard from "./common/MovieCard.vue";
import TvCard from "./common/TvCard.vue";

export default {
  name: "MainSection",
  props: {
    moviesearchresult: Array,
    tvsearchresult: Array,
  },
  components: {
    MovieCard,
    TvCard,
  },
};
</script>

<style scoped lang="scss">
#container {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-content: center;
  padding: 0 20px;
  .no-results {
    color: white;
    padding: 20px;
  }
}
</style>
