<template>
  <header>
      <div class="title">
        <h1>netflix</h1>
      </div>
      <div class="search">
        <input v-model="searchTitle" type="text" placeholder="Search..." />
        <button @click="sendSearch">
          <i class="fas fa-search"></i>
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
    },
    methods: {
      sendSearch(){
        if(this.searchTitle.trim()){
          this.$emit('search',this.searchTitle)
        }
      }
    }
}
</script>

<style lang="scss" scoped>
@mixin style-header{
  padding: .5em 1.5em;
    background-color: black;
    border: 1px solid white;
    color: white;
}

.search{
  input{
    @include style-header;
  }
  button{
    @include style-header;
    cursor: pointer;
  }
  input:focus{
    outline:none;
  }
}

</style>