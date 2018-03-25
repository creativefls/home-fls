<template>
  <v-container fluid>
    <fls-quote></fls-quote>
    <v-jumbotron color="success" dark>
      <v-container fill-height>
        <v-layout wrap>
          <v-flex md6>
            <v-card flat color="transparent">
              <h1 class="display-2">Keep in Touch</h1>
              <h1 class="headline">Official Line</h1>
              <img class="image line-barcode" src="https://user-images.githubusercontent.com/27270350/34720177-5c3e398c-f570-11e7-9aa4-2f340592da2c.jpg" alt="line barcode">
            </v-card>
          </v-flex>
          <v-flex md6>
            <v-card color="white" class="pa-2">
              <v-container fluid grid-list-sm>
                <v-layout row wrap>
                  <v-flex xs4  v-for="(insta, index) in instaFeed" :key="insta.id" v-if="index < 9">
                    <a href="https://www.instagram.com/flsummit/">
                      <img class="image" :src="insta.node.thumbnail_src" alt="flsummit" width="100%" height="100%">
                    </a>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-jumbotron>



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
            console.log('respons data: ', that.instaFeed);
          })
          .catch(function (error) {
            console.log(error);
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
</style>
