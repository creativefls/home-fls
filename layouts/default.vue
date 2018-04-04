<template>
  <v-app>
     <video autoplay muted loop id="myVideo">
      <source src="http://static.futureleadersummit.org/assets/landing_without_bumper.webm" type="video/mp4"> Your browser does not support HTML5 video.
    </video>
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
        <template v-for="item in items" >
          <v-btn v-if="item.outlink" outline round :href="item.to" :key="item.title">
            {{ item.title }}
            <v-icon size="medium" class="ml-1">{{ item.icon }}</v-icon>
          </v-btn>
          <v-btn v-else outline round :to="item.to" :key="item.title">
            {{ item.title }}
            <v-icon size="medium" class="ml-1">{{ item.icon }}</v-icon>
          </v-btn>
        </template>
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
    <v-content :class="$route.path == '/' ? 'pt-0' : ''">
      <nuxt />
    </v-content>
    <layout-footer></layout-footer>
  </v-app>
</template>

<script>
import LayoutFooter from '@/components/layouts/Footer'

export default {
  data () {
    return {
      items: [
        { icon: 'fa-backward', title: 'Recap 2017', to: '/' },
        { icon: 'fa-youtube-play', title: 'View Full Video', to: 'https://www.youtube.com/watch?v=rbIo5dDwxX4', outlink: true }
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
        return 'accent transparent'
      }
    }
  },
  methods: {
    onScroll (e) {
      this.scroll = document.documentElement.scrollTop
    }
  },
  components: { LayoutFooter }
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
      width auto !important
  .btn
    text-transform capitalize
    font-size 16px

.jumbotron
  min-height 100vh

.accent.transparent
  background-color #2c3e50cc !important

#myVideo {
  position: fixed;
  right: 0;
  top: 0;
  min-width: 100%;
  min-height: 100%;
  background-color: black;
}
</style>
