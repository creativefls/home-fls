<template>
  <v-container fluid>
    <v-container>
      <div class="display-1 text-xs-center follow">Ikuti kami</div>
      <v-layout justify-center wrap>
        <v-flex xs4 class="pa-1"  v-for="(insta, index) in instaFeed" :key="insta.id" v-if="index < 9">
          <a href="https://www.instagram.com/flsummit/">
            <img class="image" :src="insta.node.thumbnail_src" alt="flsummit" width="100%" height="100%">
          </a>
        </v-flex>
      </v-layout>

    </v-container>
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
import FlsQuote from '~/components/sections/QuoteHome'

export default {
  components: { FlsQuote },
  data () {
    return {
      instaFeed: []
    }
  },
  methods: {
    getDataInsta () {
       var that = this // this di dalam then tidak bisa bekerja
        this.$axios.get('https://www.instagram.com/flsummit/?__a=1')
          .then(function (response) {
            that.instaFeed = response.data.graphql.user.edge_owner_to_timeline_media.edges
          })
          .catch(function (error) {
            console.log('error fetch insta', error);
          });
    }
  },
  created () {
    this.getDataInsta()
  }
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
