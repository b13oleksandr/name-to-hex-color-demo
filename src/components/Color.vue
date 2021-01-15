<template>
  <div class="color">
    <div class="color__col">
      <div class="color__letter" :style="{ background: color }">
        <span>{{ letter }}</span>
      </div>
    </div>
    <div class="color__col color__col--input">
      <input
        type="text"
        class="color__input"
        :value="value"
        @input="$emit('input', $event)"
      />
      <div class="color__code">{{ color }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Color',

  props: {
    value: {
      type: String,
      default: null
    },
    color: {
      type: String,
      default: ''
    },
    letter: {
      type: String,
      default: ''
    }
  }
};
</script>

<style lang="stylus" scoped>
.color
  display flex
  margin 0 -20px
  align-items center
  @media (max-width 767px)
    flex-direction column

  &__col
    padding 0 20px

    &--input
      @media (max-width 767px)
        display flex
        flex-direction column-reverse
        align-items center
        margin-top 20px

  &__letter
    width 150px
    height 150px
    font-size 70px
    display flex
    justify-content center
    align-items center
    border-radius 50%
    color #ffffff
    background-color #5C7659

  &__input
    height 70px
    padding 0 15px
    background rgba(255, 255, 255, 0.1)
    backdrop-filter blur(4px)
    border none
    font-size 20px
    line-height 20px
    color #ffffff
    width 350px
    max-width 100%
    font-family 'Nanum Gothic', sans-serif
    margin-bottom 20px
    font-weight thin
    @media (max-width 767px)
      width 100%

  &__code
    font-size 20px
    color #ffffff
    @media (max-width 767px)
      margin-bottom 30px
</style>
