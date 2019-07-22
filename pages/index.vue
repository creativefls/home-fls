<template>
  <v-container fluid style="background-image: url('/images/background.svg'); background-repeat: no-repeat; background-size: cover">
    <!-- <img src="/images/background.svg" class="bg-hero" alt=""> -->
    <fls-hero></fls-hero>
    <fls-rooms></fls-rooms>
    <fls-theme></fls-theme>
    <fls-countdown></fls-countdown>
    <RegisterArea />
    <!-- <fls-tagline></fls-tagline> -->
    <article-post />
  </v-container>
</template>

<script>
import FlsHero from '@/components/sections/Hero'
import FlsCountdown from '@/components/sections/Countdown'
import FlsTheme from '@/components/sections/Theme'
import FlsTagline from '@/components/sections/Tagline'
import FlsRooms from '@/components/sections/Rooms'
import ArticlePost from '@/components/sections/ArticlePost'
import RegisterArea from '@/components/sections/RegisterArea'

export default {
  components: { ArticlePost, FlsHero, FlsCountdown, FlsRooms, FlsTheme, FlsTagline, RegisterArea},
  data () {
    return {
    }
  },
  computed: {
  },
  methods: {
  },
}
</script>

<style lang="stylus" scoped>
img.line-barcode {
  width auto
  height 256px
}
.section-insta
  position relative
  background: #2ecc71;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #2def7e, #2ecc71);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #2def7e, #2ecc71); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

.follow
  padding 40px
.card > *
  display block
  margin 0 auto

.bg-hero
  // background: url('/images/background-unyu.png') top center no-repeat
  // background-size: cover
  min-width 100vw
  position absolute
  top: 0
  z-index -1

</style>
