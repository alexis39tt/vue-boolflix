<template>
  <div class="tv">
    <img
      :src="`https://image.tmdb.org/t/p/w300/${elm.backdrop_path}`"
      v-if="elm.backdrop_path != null"
    />
    <img src="../../assets/unavailable.png" v-else />
    <div class="lang">
      <img
        v-show="elm.original_language == 'en'"
        src="https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg"
        :alt="elm.original_language"
      />
      <img
        v-show="elm.original_language == 'it'"
        src="https://upload.wikimedia.org/wikipedia/en/0/03/Flag_of_Italy.svg"
        :alt="elm.original_language"
      />
      <img
        v-show="elm.original_language != 'en' && elm.original_language != 'it'"
        src="https://upload.wikimedia.org/wikipedia/commons/1/11/Globe_Flag.svg"
        :alt="elm.original_language"
      />
    </div>
    <div class="title">
      <p>{{ elm.name }}</p>
    </div>
    <div class="vote">
      {{ votetransf(elm.vote_average) }}
      <font-awesome-icon
        v-for="(elm, i) in votetransf(elm.vote_average)"
        :key="i"
        icon="fa-solid fa-star"
      />
      <font-awesome-icon
        v-for="(elm, i) in 5 - votetransf(elm.vote_average)"
        :key="i"
        icon="fa-regular fa-star"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "TvCard",
  props: {
    moviesearchresult: Array,
    elm: Object,
  },
  methods: {
    votetransf(vote) {
      return Math.ceil(vote / 2);
    },
  },
};
</script>
<style lang="scss" scoped>
.tv {
  width: 300px;
  margin: 20px 5px;
  position: relative;
  cursor: pointer;
  &:hover {
    .title {
      p {
        background: rgba(255, 255, 255, 0.9);
      }
    }
  }
  img {
    width: 100%;
  }
  .lang {
    img {
      position: absolute;
      top: 5px;
      right: 5px;
      width: 25px;
    }
  }
  .title {
    position: absolute;
    bottom: 24px;
    p {
      margin: -2px 0;
      display: inline;
      background: rgba(255, 255, 255, 0.4);
      border-radius: 2px;
      padding: 0 2px;
      transition: 0.2s;
    }
  }
}
</style>