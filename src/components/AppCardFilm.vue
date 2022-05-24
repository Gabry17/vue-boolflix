<template>
  <div class="card">
    <img
      :src="'https://image.tmdb.org/t/p/w342' + filmObj.poster_path"
      :alt="filmObj.original_title"
    />
    <div class="text">
      <p>
        Titolo:<br />
        {{ filmObj.title }}
      </p>
      <p :class="{remove: filmObj.title.toLowerCase() === filmObj.original_title.toLowerCase() }">
        Titolo originale:<br />
        {{ filmObj.original_title }}
      </p>
      <p>
        Lingua:<br />
        {{ lang }}
      </p>
      <p>
        Descizione:<br />
        {{ filmObj.overview }}
      </p>
      <div class="star">
        <p>Voto:</p>
        <div class="icon">
          <p v-for="(star, index) in this.vote" :key="index">
            <i class="fas fa-star"></i>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppCardFilm",
  data() {
    return {
      vote: 0,
      lang: "",
      
    };
  },
  mounted() {
    if (this.filmObj.vote_average > 0) {
      this.vote = Math.ceil(this.filmObj.vote_average / 2);
    } else {
      this.vote = 1;
    }

    if (this.filmObj.original_language === "it") {
      this.lang = "🇮🇹";
    } else if (this.filmObj.original_language === "en") {
      this.lang = "🇬🇧";
    } else {
      this.lang = this.filmObj.original_language;
    }
  },
  props: {
    filmObj: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "../style/card.scss";
</style>
