<template>
  <main>
    <div class="container">
        <AppCardFilm v-for="element in filmList" :key="element.id" :filmObj="element" />
    </div>
  </main>
</template>

<script>
import AppCardFilm from "./AppCardFilm.vue";

export default {
  name: "AppMain",
  components: {
    AppCardFilm,
  },
  props:{
      filmList: Array
  }
};
</script>

<style lang="scss" scoped>
main {
  background-color: #2d2c2c;
  height: calc(100vh - 100px);
  .container {
    width: 80%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
  }
}
</style>
