<template>
  <main>
    <h2 @click="viewCast">film</h2>
    <div class="container">
      <AppCardFilm
        v-for="element in filmList"
        :key="element.id"
        :filmObj="element"
        :castList="castFilm"
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
import axios from 'axios';

export default {
  name: "AppMain",
  components: {
    AppCardFilm,
    AppCardSerie,
  },
  props: {
    filmList: Array,
    serieList: Array,
  },
  data(){
    return{
      castFilm: []
    }
  },
  methods: {
    viewCast(){
      this.filmList.forEach((e) => {
            axios
              .get(`https://api.themoviedb.org/3/movie/${e.id}/credits`, {
                params:{
                  api_key: "cda791e52a23bffc861ee9b7107cfc69",
          query: this.searchTitle
                }
              } )
              .then((resp) => {
                this.castFilm = resp.data.cast;
                console.log(this.castFilm);
              });
          });
    }
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
  i{
    color: white;
  }
  
  
}
</style>
