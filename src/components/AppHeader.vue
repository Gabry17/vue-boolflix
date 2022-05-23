<template>
  <header>
      <div class="title">
        <h1>netflix</h1>
      </div>
      <div class="search">
        <input v-model="searchTitle" type="text" placeholder="titolo film" />
        <button @click="$emit('search',searchTitle)">
          cerca
        </button>
      </div>
    </header>
</template>

<script>
export default {
    name: 'AppHeader',
    data(){
        return{
            searchTitle: ''
        }
    }
}
</script>

<style lang="scss" scoped>

</style>