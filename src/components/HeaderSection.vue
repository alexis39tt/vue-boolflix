<template>
  <header>
    <input type="text" v-model="moviename" @keydown.enter="$emit('search', moviename)">
    <button @click="$emit('search', moviename)">Cerca</button>
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
