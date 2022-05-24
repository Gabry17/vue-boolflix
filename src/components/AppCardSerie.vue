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
      <p>
        Titolo originale:<br />
        {{ serieObj.original_name }}
      </p>
      <p>
        Lingua:<br />
        {{ lang }}
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
.card {
  position: relative;
  .text {
    position: absolute;
    top: 0;
    left: 0;
    display: none;
    background-color: black;
    height: 100%;
    width: 100%;
    overflow: auto;
    padding: 1em;
  }
}
.card:hover .text {
  display: block;
}
.star i {
  color: #e3e319;
}
.star {
  display: flex;
  flex-direction: column;
  .icon {
    display: flex;
    justify-content: center;
  }
}
</style>
