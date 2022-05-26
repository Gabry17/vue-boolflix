<template>
  <div class="card">
    <img :src="img" :alt="filmObj.title" />
    <div class="text">
      <p>
        Titolo:<br />
        {{ filmObj.title }}
      </p>
      <p :class="{ remove: filmObj.title.toLowerCase() === filmObj.original_title.toLowerCase() }">
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
      <p>Cast:<br /></p>
      <ul>
        <li v-for="(actor, index) in filmObj.cast" :key="index">
          {{ actor.name }}
        </li>
      </ul>
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
      img: "",
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

    if (this.filmObj.poster_path === null) {
      return (this.img =
        "data:image/png;base64,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");
    } else {
      return (this.img =
        "https://image.tmdb.org/t/p/w342" + this.filmObj.poster_path);
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
