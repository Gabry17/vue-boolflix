<template>
  <div class="card">
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
    props: {
        filmObj: Object
    }
}
</script>

<style lang="scss" scoped>
.card{
    color: white;
    text-align: center;
    width: calc(100% / 5 - 30px);
    margin: 15px;
}

</style>