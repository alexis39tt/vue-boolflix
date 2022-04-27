<template>
  <div class="outer">
    <div class="tv">
      <div class="front">
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
            v-show="
              elm.original_language != 'en' && elm.original_language != 'it'
            "
            src="https://upload.wikimedia.org/wikipedia/commons/1/11/Globe_Flag.svg"
            :alt="elm.original_language"
          />
        </div>
        <div class="title">
          <p>{{ elm.name }}</p>
        </div>
      </div>
      <div class="overlay back">
        <h3>{{ elm.original_name }}</h3>
        <div class="vote">
          <div v-if="votetransf(elm.vote_average) != 0">
            <font-awesome-icon
              v-for="(elm, i) in votetransf(elm.vote_average)"
              :key="'a' + elm.name + i"
              icon="fa-solid fa-star"
              class="full-stars"
            />
            <font-awesome-icon
              v-for="(elm, i) in 5 - votetransf(elm.vote_average)"
              :key="'b' + elm.name + i"
              icon="fa-regular fa-star"
              class="empty-stars"
            />
          </div>
          <div v-else>
            <p class="no-vote">No rating</p>
          </div>
        </div>
        <p v-if="elm.overview" class="overview">{{ elm.overview }}</p>
        <p v-else class="overview">Descrizione non disponibile</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TvCard",
  props: {
    tvsearchresult: Array,
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
.outer {
  perspective: 1000px;
  &:hover {
    .tv {
      transform: rotateX(180deg);
    }
  }
}
.front,
.back {
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.back {
  transform: rotateX(180deg);
}
.tv {
  width: 300px;
  margin: 20px 5px;
  position: relative;
  cursor: pointer;
  transition: transform 0.5s;
  transform-style: preserve-3d;
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
    bottom: 4px;
    p {
      margin: 0;
      display: inline;
      background: rgba(255, 255, 255, 0.4);
      border-radius: 2px;
      padding: 0 2px;
      transition: 0.2s;
    }
  }
}
.vote {
  .full-stars {
    color: #ffbb01;
  }
  .empty-stars{
    color: gray;
  }
  .no-vote {
    color: #ff7301;
  }
}
.overlay {
  position: absolute;
  padding: 5px 5px;
  margin-bottom: -5px;
  width: 100%;
  height: 169px;
  bottom: 5px;
  background: rgb(0, 0, 0);
  overflow: auto;
  p,
  h3 {
    color: white;
  }
  .overview {
    margin-top: 10px;
    font-size: 0.8rem;
  }
}
</style>