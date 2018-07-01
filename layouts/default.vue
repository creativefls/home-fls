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
      <nuxt-link to="/" class="hidden-md-and-up">
        <v-toolbar-title>
          <v-avatar tile>
            <img src="https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png" alt="FLS Logo">
          </v-avatar>
        </v-toolbar-title>
      </nuxt-link>
      <v-spacer class="hidden-md-and-up"></v-spacer>
      <v-toolbar-items class="align-center hidden-sm-and-down" style="margin-left: auto">
        <!-- <nuxt-link to="/">
          <v-avatar tile>
            <img src="https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png" alt="FLS Logo">
          </v-avatar>
        </nuxt-link> -->
        <template v-for="(item, i ) in items" >
          <v-btn v-if="item.outlink" flat :href="item.to" :key="item.title">
            {{ item.title }}
          </v-btn>
          <v-btn v-else flat :to="item.to" :key="item.title">
            {{ item.title }}
          </v-btn>
          <nuxt-link :key="i" v-if="i+1 == (items.length/2)" to="/" class="px-4 py-2">
            <v-avatar tile>
              <img src="https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png" alt="FLS Logo">
            </v-avatar>
          </nuxt-link>
        </template>
      </v-toolbar-items>
      <v-btn
        icon
        class="hidden-md-and-up"
        @click.stop="navDrawer = !navDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>

    <v-content :class="$route.path == '/' ? 'pt-0' : 'padding-page'" v-scroll="onScroll">
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
        { title: 'Program', to: '/program', outlink: false },
        { title: 'Galeri', to: '/2017/galeri', outlink: true },
        { title: 'Kilas Balik', to: '/kilas-balik', outlink: true },
        { title: 'Artikel', to: '/artikel', outlink: false }
      ],
      navDrawer: false,
      scroll: 0
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
  .v-avatar--tile
    height 36px !important
    width auto !important
  .v-btn
    text-transform capitalize
    font-size 16px

.accent.transparent
  background-color #2c3e50 !important

.padding-page
  padding-top 60px !important
</style>
