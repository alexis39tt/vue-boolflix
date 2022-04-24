<template>
  <main>
    <div id="moviescontainer">
      <div v-for="(elm, i) in moviesearchresult" :key="i" class="movie">
        <img
          :src="`https://image.tmdb.org/t/p/w185/${elm.poster_path}`"
          :alt="elm.title"
        />
        <div class="lang">
          <img v-show="elm.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg" :alt="elm.original_language">
          <img v-show="elm.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/en/0/03/Flag_of_Italy.svg" :alt="elm.original_language">
          <img v-show="elm.original_language == 'xx' || ''" src="https://upload.wikimedia.org/wikipedia/commons/1/11/Globe_Flag.svg" :alt="elm.original_language">
        </div>
        
        {{ elm.title }} - {{ elm.original_title }}
        <div class="vote">
          {{ votetransf(elm.vote_average) }}
            <font-awesome-icon v-for="elm, i in votetransf(elm.vote_average)" :key="i" icon="fa-solid fa-star" />
            <font-awesome-icon v-for="elm, i in 5-votetransf(elm.vote_average)" :key="i" icon="fa-regular fa-star" />
          </div>
        </div>
      </div>
    <div id="tvseriescontainer">
      <div v-for="(elm, i) in tvsearchresult" :key="i" class="tv">
        <img
          :src="`https://image.tmdb.org/t/p/w185/${elm.poster_path}`"
          :alt="elm.title"
        />
        <div class="lang">
          <img v-show="elm.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg" :alt="elm.original_language">
          <img v-show="elm.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/en/0/03/Flag_of_Italy.svg" :alt="elm.original_language">
          <img v-show="elm.original_language == 'xx' || ''" src="https://upload.wikimedia.org/wikipedia/commons/1/11/Globe_Flag.svg" :alt="elm.original_language">
        </div>
        
        {{ elm.name }} - {{ elm.original_name }}


        <div class="vote">
          {{ votetransf(elm.vote_average) }}
            <font-awesome-icon v-for="elm, i in votetransf(elm.vote_average)" :key="i" icon="fa-solid fa-star" />
            <font-awesome-icon v-for="elm, i in 5-votetransf(elm.vote_average)" :key="i" icon="fa-regular fa-star" />
          </div>
        
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainSection",
  props: {
    moviesearchresult: Array,
    tvsearchresult: Array
  },
  methods: {
    votetransf(vote){
      return Math.ceil(vote/2)
    }
  }
};
</script>

<style scoped lang="scss">
</style>
