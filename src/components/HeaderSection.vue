<template>
  <header>
    <div id="logo">
      <img
        src="https://image.tmdb.org/t/p/w185/wwemzKWzjKYJFfCeiB57q3r4Bcm.png"
        alt="logo"
      />
    </div>
    <div id="search">
      <input
        type="text"
        v-model.trim="moviename"
        @keydown.enter="$emit('search', moviename)"
        placeholder="Cerca un film..."
      />
      <button @click="$emit('search', moviename)">
        <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderSection",
  data() {
    return {
      moviename: "",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  display: flex;
  justify-content: space-between;
  height: 70px;
  #logo {
    margin: auto 10px;
  }
  #search {
    margin: auto 10px;
    input {
      color: gray;
      line-height: 1.2rem;
      font-size: 1.2rem;
      padding: 2px 5px;
      border: 2px solid gray;
      border-radius: 2px;
      outline: none;
      background-color: black;
      margin-right: 10px;
    }
    button {
      color: gray;
      line-height: 1.4rem;
      font-size: 1.2rem;
      padding: 2px 5px;
      border: 2px solid gray;
      border-radius: 2px;
      outline: none;
      background-color: black;
      cursor: pointer;
    }
  }
}
</style>
