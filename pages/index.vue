<template>
  <v-container fluid>
    <div style="background: url('/images/background-unyu.png') top center no-repeat; background-size: 100%;">
      <fls-hero></fls-hero>
      <fls-countdown></fls-countdown>
    </div>
    <fls-rooms></fls-rooms>
    <article-post />
  </v-container>
</template>

<script>
import FlsHero from '@/components/sections/Hero'
import FlsCountdown from '@/components/sections/Countdown'
import FlsRooms from '@/components/sections/Rooms'
import ArticlePost from '@/components/sections/ArticlePost'

export default {
  components: { ArticlePost, FlsHero, FlsCountdown, FlsRooms },
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
</style>
