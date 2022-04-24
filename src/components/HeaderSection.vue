<template>
  <header>
    <div id="logo">
      <img src="https://image.tmdb.org/t/p/w185/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="logo">
    </div>
    <div id="search">
      <input type="text" v-model.trim="moviename" @keydown.enter="$emit('search', moviename)">
      <button @click="$emit('search', moviename)">Cerca</button>
      </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderSection',
  data(){
    return{
      moviename: ''
    }
  }
}
</script>

<style scoped lang="scss">

</style>
