<template>
  <v-app>
    <v-navigation-drawer
      temporary
      v-model="navDrawer"
      fixed>
      <v-list>
        <v-list-tile
          router
          :to="item.to"
          :key="i"
          v-for="(item, i) in items"
          exact>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar :color="toolbarColor" class="d-flex" scroll-off-screen dense flat dark app>
      <nuxt-link to="/">
        <v-toolbar-title>
          <v-avatar tile>
            <img src="https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png" alt="FLS Logo">
          </v-avatar>
        </v-toolbar-title>
      </nuxt-link>
      <v-spacer></v-spacer>
      <div class="align-center hidden-sm-and-down" style="margin-left: auto">
        <v-btn outline>
          Recap 2017
          <v-icon size="medium" class="ml-1">fa-backward</v-icon>
        </v-btn>
        <v-btn outline href="https://www.youtube.com/watch?v=rbIo5dDwxX4">
          View Full Video
          <v-icon size="medium" class="ml-1">fa-youtube-play</v-icon>
        </v-btn>
      </div>
      <v-btn
        icon
        class="hidden-md-and-up"
        @click.stop="navDrawer = !navDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>
    <v-jumbotron
      v-if="$route.path == '/'"
      src="https://vuetifyjs.com/static/doc-images/parallax/material2.jpg"
      :gradient="gradient"
      v-scroll="onScroll"
      dark >
      <v-container fill-height>
        <v-layout align-center>
          <v-flex text-xs-center>
            <h3 class="display-3">Ready for being a Leader?</h3>
          </v-flex>
        </v-layout>
      </v-container>
    </v-jumbotron>
    <v-content>
      <nuxt />
    </v-content>
    <v-footer>
      <span>&copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      items: [
        { title: 'Welcome', to: '/' },
        { title: 'Inspire', to: '/inspire' }
      ],
      navDrawer: false,
      scroll: 0,
      gradient: 'to top right, rgba(63,81,181, .7), rgba(25,32,72, .7)'
    }
  },
  computed: {
    toolbarColor () {
      if (this.scroll < 50 && this.$route.path == '/') {
        return 'transparent'
      } else {
        return 'dark'
      }
    }
  },
  methods: {
    onScroll (e) {
      this.scroll = document.documentElement.scrollTop
    }
  }
}
</script>

<style lang="stylus">
nav
  justify-content center
  padding 6px 0
  .toolbar__content
    @media only screen and (min-device-width: 960px)
      max-width 80%
  .toolbar__title
    margin-left 0
    .avatar.avatar--tile
      height 36px !important
      width 100% !important
  .btn
    text-transform capitalize
    font-size 16px
    font-weight 400

.jumbotron
  min-height 100vh
</style>
