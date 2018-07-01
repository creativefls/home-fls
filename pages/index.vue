<template>
  <v-container fluid>
    <img src="/images/background-unyu.png" class="bg-hero" alt="">
    <fls-hero></fls-hero>
    <fls-countdown></fls-countdown>
    <fls-theme></fls-theme>
    <fls-tagline></fls-tagline>
    <fls-rooms></fls-rooms>
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

export default {
  components: { ArticlePost, FlsHero, FlsCountdown, FlsRooms, FlsTheme, FlsTagline },
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
  min-width 100%
  position absolute
  top: 0
  z-index -1

</style>
