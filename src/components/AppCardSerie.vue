<template>
  <div class="card">
      <img :src="'https://image.tmdb.org/t/p/w342' + serieObj.poster_path" alt="">
      <h3>{{ serieObj.name }}</h3>
      <p>{{ serieObj.original_name }}</p>
      <p v-if="serieObj.original_language === 'it'">🇮🇹</p>
      <p v-if="serieObj.original_language === 'en'">🇬🇧</p>
      <p v-if="serieObj.original_language !== 'it' && serieObj.original_language !== 'en'">{{ serieObj.original_language }}</p>
      <p>{{ serieObj.vote_average }}</p>
  </div>
</template>

<script>
export default {
    name: 'AppCardSerie',
    props: {
        serieObj: Object
    }
}
</script>

<style lang="scss" scoped>

</style>