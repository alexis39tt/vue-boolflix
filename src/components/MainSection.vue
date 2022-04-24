<template>
  <main>
    <div id="moviescontainer">
      <div v-for="(elm, i) in searchresult" :key="i" class="movie">
        <img
          :src="`https://image.tmdb.org/t/p/w185/${elm.poster_path}`"
          :alt="elm.title"
        />
        <div class="lang">
          <img v-show="elm.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg" :alt="elm.original_language">
          <img v-show="elm.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/en/0/03/Flag_of_Italy.svg" :alt="elm.original_language">
          <img v-show="elm.original_language == 'xx' || ''" src="https://upload.wikimedia.org/wikipedia/commons/1/11/Globe_Flag.svg" :alt="elm.original_language">
        </div>
        
        {{ elm.title }} - {{ elm.original_title }} - {{ elm.vote_average }}
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
