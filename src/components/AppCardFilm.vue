<template>
  <div class="card">
      <img :src="'https://image.tmdb.org/t/p/w342' + filmObj.poster_path" :alt="filmObj.original_title">
      <h3>{{ filmObj.title }}</h3>
      <p>{{ filmObj.original_title }}</p>
      <p>{{ lang }}</p>
      <div class="star">
          <p v-for="(star , index) in this.vote" :key="index"><i class="fas fa-star"></i></p>
      </div>
  </div>
</template>

<script>
export default {
    name: 'AppCardFilm',
    data(){
        return{
            vote: 0,
             lang: ''
        }
    },
    mounted() {
    if (this.filmObj.vote_average > 8) {
      this.vote = 5;
    } else if (
      this.filmObj.vote_average > 6 &&
      this.filmObj.vote_average < 9
    ) {
      this.vote = 4;
    } else if (
      this.filmObj.vote_average > 4 &&
      this.filmObj.vote_average < 7
    ) {
      this.vote = 3;
    } else if (
      this.filmObj.vote_average > 2 &&
      this.filmObj.vote_average < 5
    ) {
      this.vote = 2;
    } else {
      this.vote = 1;
    }

    if(this.filmObj.original_language === 'it'){
        this.lang = '🇮🇹'
    } else if (this.filmObj.original_language === 'en'){
        this.lang = '🇬🇧'
    } else {
        this.lang = this.filmObj.original_language
    }
    },
    props: {
        filmObj: Object
    }
}
</script>

<style lang="scss" scoped>
.star{
    color: #e3e319;
    display: flex;
}
</style>