<template>
  <div class="links">
    <div class="links__col">
      <a href="https://www.npmjs.com/package/name-to-hex-color" target="_blank">
        <img src="@/assets/npm.png" alt="npm">
      </a>
    </div>
    <div class="links__col">
      <a href="https://github.com/b13oleksandr/name-to-hex-color" target="_blank">
        <img src="@/assets/github.png" alt="github">
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Links'
};
</script>

<style lang="stylus" scoped>
.links
  margin 0 -30px
  display inline-flex
  align-items center

  &__col
    padding 0 30px
</style>
