<template>
  <header>
      <div class="title">
          <h1>netflix</h1>
      </div>
      <div class="search">
          <input type="text" placeholder="titolo film">
          <button>cerca</button>
      </div>
  </header>
</template>

<script>
export default {
    name: 'AppHeader'
}
</script>

<style lang="scss" scoped>
header{
    background-color: black;
    padding: 0 1em;
    display: flex;
    justify-content: space-between;
    line-height: 100px;
    .title{
        color: red;
        text-transform: uppercase;
    }
}
</style>