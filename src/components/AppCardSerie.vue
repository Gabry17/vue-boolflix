<template>
  <div class="card">
    <img
      :src="'https://image.tmdb.org/t/p/w342' + serieObj.poster_path"
      :alt="serieObj.original_name"
    />
    <div class="text">
      <p>
        <span>Titolo:</span><br />
        {{ serieObj.name }}
      </p>
      <p :class="{remove: serieObj.name.toLowerCase() === serieObj.original_name.toLowerCase() }">
        Titolo originale:<br />
        {{ serieObj.original_name }}
      </p>
      <p>
        Lingua:<br />
        {{ lang }}
      </p>
      <p>
        Descizione:<br />
        {{ serieObj.overview }}
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
  name: "AppCardSerie",
  data() {
    return {
      vote: 0,
      lang: "",
    };
  },
  props: {
    serieObj: Object,
  },
  mounted() {
    if (this.serieObj.vote_average > 0) {
      this.vote = Math.ceil(this.serieObj.vote_average / 2);
    } else {
      this.vote = 1;
    }

    if (this.serieObj.original_language === "it") {
      this.lang = "🇮🇹";
    } else if (this.serieObj.original_language === "en") {
      this.lang = "🇬🇧";
    } else {
      this.lang = this.serieObj.original_language;
    }
  },
};
</script>

<style lang="scss" scoped>
@import "../style/card.scss";
</style>
