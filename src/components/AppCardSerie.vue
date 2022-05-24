<template>
  <div class="card">
    <img
      :src="'https://image.tmdb.org/t/p/w342' + serieObj.poster_path"
      :alt="serieObj.original_name"
    />
    <h3>{{ serieObj.name }}</h3>
    <p>{{ serieObj.original_name }}</p>
    <p>{{ lang }}</p>
    <div class="star">
          <p v-for="(star , index) in this.vote" :key="index"><i class="fas fa-star"></i></p>
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
      if(this.serieObj.vote_average > 0){
          this.vote = Math.ceil(this.serieObj.vote_average / 2);
      } else {
          this.vote = 1;
      }
    
    if(this.serieObj.original_language === 'it'){
        this.lang = '🇮🇹'
    } else if (this.serieObj.original_language === 'en'){
        this.lang = '🇬🇧'
    } else {
        this.lang = this.serieObj.original_language
    }
  },
};
</script>

<style lang="scss" scoped>
.star{
    color: #e3e319;
    display: flex;
}
</style>
