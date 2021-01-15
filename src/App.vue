<template>
  <div class="demo" :style="{ background: bgColor }">
    <div class="demo__container">
      <div class="demo__big-letter" :style="{ background: color }">
        <span>{{ letter }}</span>
      </div>

      <div class="demo__glass">
        <div class="demo__glass-blur" />
        <div class="demo__glass-inner">
          <div class="demo__glass-content">
            <div class="demo__color">
              <Color
                :letter="letter"
                :color="color"
                :value="name"
                @input="name = $event.target.value"
              />
            </div>
          </div>

          <div class="demo__links">
            <Links />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';
import { nameToHexColor } from 'name-to-hex-color';
import Color from '@/components/Color.vue';
import Links from '@/components/Links.vue';

// eslint-disable-next-line @typescript-eslint/no-var-requires
const makeColor = require('color');

const DEFAULT_NAME = 'Bender Bending Rodríguez';

export default defineComponent({
  name: 'App',

  components: {
    Links,
    Color
  },

  setup() {
    const name = ref(DEFAULT_NAME);
    const color = computed(() => nameToHexColor(name.value));
    const letter = computed(() => name.value.slice(0, 1).toUpperCase());
    const bgColor = computed(() => makeColor(color.value).darken(0.5));

    return {
      name,
      color,
      letter,
      bgColor
    };
  }
});
</script>

<style lang="stylus">
@import url('https://fonts.googleapis.com/css2?family=Nanum+Gothic&display=swap')

body
  padding 0
  margin 0
  font-family 'Nanum Gothic', sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale

*
  box-sizing border-box
  outline none

.demo
  background-color #2E3B2D
  padding 30px 20px
  min-height 100vh
  display flex

  &__container
    width 1400px
    max-width 100%
    margin auto
    position relative
    display flex
    align-items center
    justify-content center

  &__big-letter
    width 410px
    height @width
    background-color #5C7659
    border-radius 50%
    display flex
    align-items center
    justify-content center
    font-size 250px
    color #ffffff
    position absolute
    top 50%
    transform translateY(-50%)
    left 0
    @media (max-width 767px)
      left 50%
      top 0
      transform translate(-50%, 0)
      width 290px
      height @width

  &__big-letter-shadow
    width 294.72px
    height 378.37px
    background #5C7659
    filter blur(100px)
    transform rotate(-1.31deg)
    position absolute
    left 135px

  &__glass
    width 930px
    max-width 100%
    position relative
    @media (max-width 767px)
      margin-top 180px

  &__glass-blur
    position absolute
    left 0
    top 0
    right 0
    bottom 0
    background rgba(255, 255, 255, 0.03)
    box-shadow inset 0 0 40px rgba(255, 255, 255, 0.25)
    backdrop-filter blur(15px)

  &__glass-inner
    padding 80px
    position relative
    @media (max-width 767px)
      padding 50px 44px

  &__glass-content
    display flex
    padding 140px 0 144px
    @media (max-width 1023px)
      justify-content center
    @media (max-width 767px)
      padding 0 0 144px

  &__color
    margin-left 120px

    @media (max-width 1023px)
      margin-left 0

  &__links
    display flex
    justify-content flex-end
    @media (max-width 767px)
      justify-content center
</style>
