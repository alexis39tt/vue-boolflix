<template>
  <main>
      <ul>
          <li v-for="(elm, i) in searchresult" :key="i">{{ elm.original_title }}</li>
      </ul>
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
