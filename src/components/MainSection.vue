<template>
  <main>
    <div id="moviescontainer">
      <div v-for="(elm, i) in searchresult" :key="i" class="movie">
        <img
          :src="`https://image.tmdb.org/t/p/w185/${elm.poster_path}`"
          :alt="elm.title"
        />
        {{ elm.title }} - {{ elm.original_title }} -
        {{ elm.original_language }} - {{ elm.vote_average }}
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainSection",
  props: {
    searchresult: Array,
  },
};
</script>

<style scoped lang="scss">
</style>
