<template>
  <main>
    <h2>film</h2>
    <div class="container">
      <AppCardFilm
        v-for="(element,index) in filmList"
        :key="index"
        :filmObj="element"
      />
      
    </div>
    <h2>serie</h2>
    <div class="container">
      <AppCardSerie v-for="elem in serieList" :key="elem.id" :serieObj="elem" />
    </div>
  </main>
</template>

<script>
import AppCardFilm from "./AppCardFilm.vue";
import AppCardSerie from "./AppCardSerie.vue";

export default {
  name: "AppMain",
  components: {
    AppCardFilm,
    AppCardSerie,
  },
  props: {
    filmList: Array,
    serieList: Array,
  }
};
</script>

<style lang="scss" scoped>
@import "../style/card.scss";
main {
  background-color: #2d2c2c;
  height: calc(100vh - 100px);
  overflow: scroll;
  text-align: center;
  h2 {
    color: red;
    text-transform: uppercase;
    margin-left: 1em;
    padding: 1em 0;
  }
  .container {
    width: 80%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
  }
  
  
}
</style>
