<template>
  <v-container fluid>
    <div style="background: url('/images/background-unyu.png') top center / contain no-repeat">
      <fls-hero></fls-hero>
      <fls-countdown></fls-countdown>
    </div>
    <article-post />
    <v-layout class="section-insta success" wrap justify-center>
      <v-flex align-content-center="" md6 class="pb-5">
        <v-card flat dark color="transparent">
          <h1 class="headline text-xs-center follow">Official Line</h1>
          <img class="image line-barcode" src="https://user-images.githubusercontent.com/27270350/34720177-5c3e398c-f570-11e7-9aa4-2f340592da2c.jpg" alt="line barcode">
        </v-card>
      </v-flex>

    </v-layout>
  </v-container>
</template>

<script>
import FlsHero from '@/components/sections/Hero'
import FlsCountdown from '@/components/sections/Countdown'
import ArticlePost from '@/components/sections/ArticlePost'

export default {
  components: { ArticlePost, FlsHero, FlsCountdown },
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
