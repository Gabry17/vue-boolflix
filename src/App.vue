<template>
  <div id="app">
    <!-- header -->
    <header>
      <div class="title">
        <h1>netflix</h1>
      </div>
      <div class="search">
        <input type="text" placeholder="titolo film" />
        <button @click="viewFilm">
          cerca
        </button>
      </div>
    </header>
    <!-- /header -->

    <!-- main -->
    <AppMain :filmList="film" />
    <!-- /main -->
  </div>
</template>

<script>
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppMain,
  },
  data() {
    return {
      film: []
    };
  },
  methods: {
    viewFilm() {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=cda791e52a23bffc861ee9b7107cfc69&query=l"
        )
        .then((resp) => {
          this.film = resp.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
