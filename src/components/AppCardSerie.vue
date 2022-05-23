<template>
  <div class="card">
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