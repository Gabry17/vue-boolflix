<template>
  <div >{{ castObj.name }}</div>
</template>

<script>
export default {
  name: "AppCastFilm",
  props: {
    castObj: Object,
  }
};
</script>

<style lang="scss" scoped>
div{
  color: white;
}
</style>
