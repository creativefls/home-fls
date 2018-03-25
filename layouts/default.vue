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
    <v-toolbar :color="toolbarColor" class="d-flex" scroll-off-screen flat dark app>
      <v-toolbar-title>
        <v-avatar tile>
          <img src="https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png" alt="FLS Logo">
        </v-avatar>
        <!-- <v-btn icon>
        </v-btn> -->
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn flat>Link One</v-btn>
        <v-btn flat>Link Two</v-btn>
        <v-btn flat>Link Three</v-btn>
      </v-toolbar-items>
      <v-btn
        icon
        class="hidden-md-and-up"
        @click.stop="navDrawer = !navDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>
    <v-jumbotron
      src="https://vuetifyjs.com/static/doc-images/parallax/material2.jpg"
      :gradient="gradient"
      v-scroll="onScroll"
      dark >
      <v-container fill-height>
        <v-layout align-center>
          <v-flex text-xs-center>
            <h3 class="display-3">Gradient over Image {{ toolbarColor }} </h3>
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
      if (this.scroll > 50) {
        return 'primary'
      } else {
        return 'transparent'
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
  .toolbar__content
    @media only screen and (min-device-width: 960px)
      max-width 80%
  .toolbar__title
    .avatar.avatar--tile
      height 36px !important
      width 100% !important
  .btn
    text-transform capitalize

.jumbotron
  min-height 100vh
</style>
