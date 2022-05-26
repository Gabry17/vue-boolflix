<template>
  <div id="app">
    <!-- header -->
    <AppHeader @search="viewFilm($event)" />
    <!-- /header -->

    <!-- main -->
    <img class="sfondo" :class="{none: film.length > 1}" src="./assets/img/netflix-xboxone-5c0baa4646e0fb00010dcf1c.jpeg" alt="">
    <div class="none" :class="{block: film.length > 1}" >
      <AppMain :filmList="film" :serieList="serie" />
    </div>
    <!-- /main -->
  </div>
</template>

<script>
import AppMain from "./components/AppMain.vue";
import AppHeader from "./components/AppHeader.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppMain,
    AppHeader,
  },
  data() {
    return {
      film: [],
      serie: []
    };
  },
  methods: {
    viewFilm(searchTitle) {
      const options = {
        params: {
          api_key: "cda791e52a23bffc861ee9b7107cfc69",
          query: searchTitle,
        },
      };

      this.film = [];
      axios
        .get("https://api.themoviedb.org/3/search/movie", options)
        .then((resp) => {
          const film = resp.data.results;
          
          film.forEach(item => {
            axios
              .get(`https://api.themoviedb.org/3/movie/${item.id}/credits`, options )
              .then((resp) => {
                item.cast = resp.data.cast.splice(0, 5);
                this.film.push(item);
              });
          });
        });


      this.serie = [];
      axios
        .get("https://api.themoviedb.org/3/search/tv", options)
        .then((resp) => {
          //this.serie = resp.data.results;
          const serie = resp.data.results;
          
          serie.forEach(item => {
            axios
              .get(`https://api.themoviedb.org/3/movie/${item.id}/credits`, options )
              .then((resp) => {
                item.cast = resp.data.cast.splice(0, 5);
                this.serie.push(item);
              });
          });
        });
    }
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
@import "~@fortawesome/fontawesome-free/css/all.min.css";
.sfondo{
  height: calc(100vh - 100px);
}
.none{
  display: none;
}
.block{
  display: block;
}
</style>
