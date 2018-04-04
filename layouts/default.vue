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
      :gradient="gradientJumbotron"
      v-scroll="onScroll"
      dark >
      <v-container fill-height>
        <v-layout align-center>
          <v-flex text-xs-center>
            <h1 class="display-3">
              The Future is Never Set;
              <br> It is Ours to Create
            </h1>
            <h2 class="subtitle">
              &mdash;
            </h2>
            <v-btn href="/artikel" color="error" large round depressed>Take Your First Move</v-btn>
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
        { icon: 'fa-backward', title: 'Recap 2017', to: 'https://www.youtube.com/watch?v=rbIo5dDwxX4', outlink: true },
        // { icon: 'fa-youtube-play', title: 'View Full Video', to: 'https://www.youtube.com/watch?v=rbIo5dDwxX4', outlink: true }
      ],
      navDrawer: false,
      scroll: 0,
      gradientJumbotron: 'to right, #da22ff, #9733ee'
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
  .display-3
    @media only screen and (max-device-width: 960px)
      font-size 40px !important

.accent.transparent
  background-color #2c3e50cc !important

</style>
