<template>
  <div class="card">
      <img :src="'https://image.tmdb.org/t/p/w342' + filmObj.poster_path" alt="">
      <h3>{{ filmObj.title }}</h3>
      <p>{{ filmObj.original_title }}</p>
      <p v-if="filmObj.original_language === 'it'">🇮🇹</p>
      <p v-if="filmObj.original_language === 'en'">🇬🇧</p>
      <p v-if="filmObj.original_language !== 'it' && filmObj.original_language !== 'en'">{{ filmObj.original_language }}</p>
      <p>{{ filmObj.vote_average }}</p>
  </div>
</template>

<script>
export default {
    name: 'AppCardFilm',
    urlImg: 'https://image.tmdb.org/t/p/w342',
    props: {
        filmObj: Object
    }
}
</script>

<style lang="scss" scoped>

</style>