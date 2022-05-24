<template>
  <div id="app">
    <!-- header -->
    <AppHeader @search="viewFilm($event)" />
    <!-- /header -->

    <!-- main -->
    <AppMain :filmList="film" :serieList="serie" />
    <!-- /main -->
  </div>
</template>

<script>
import AppMain from "./components/AppMain.vue";
import AppHeader from "./components/AppHeader.vue"
import axios from "axios";

export default {
  name: "App",
  components: {
    AppMain,
    AppHeader
  },
  data() {
    return {
      film: [],
      serie: []
    };
  },
  methods: {
    viewFilm(searchTitle) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie",{
            params:{
              api_key: 'cda791e52a23bffc861ee9b7107cfc69',
              query: searchTitle
            }
          }
        )
        .then((resp) => {
          this.film = resp.data.results;
        });

        axios
        .get(
          "https://api.themoviedb.org/3/search/tv",{
            params:{
              api_key: 'cda791e52a23bffc861ee9b7107cfc69',
              query: searchTitle
            }
          }
        )
        .then((resp) => {
          this.serie = resp.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
@import '~@fortawesome/fontawesome-free/css/all.min.css';
</style>
