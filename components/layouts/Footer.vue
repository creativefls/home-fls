<template>
  <v-footer height="auto">
    <v-card flat tile>
      <v-card-title v-if="false" class="primary white--text">
        <v-container>
          <strong class="subheading">Ingin mendapatkan informasi terbaru seputar Future Leader Summit ? Ikuti kami</strong>
          <v-spacer></v-spacer>
          <v-btn
            v-for="icon in icons"
            :key="icon.name"
            icon
            dark
            :href="icon.link"
            class="mx-3">
            <v-icon size="24px">{{ icon.name }}</v-icon>
          </v-btn>
        </v-container>
      </v-card-title>
      <v-card-text class="cloud">
        <v-container>
          <v-layout wrap class="text-xs-center">
            <v-flex class="pa-3" md4>
              <p class="subheading">HUBUNGI KAMI</p>
              <div>
                <v-icon size="small" class="mr-1">fa-envelope</v-icon>
                info[at]futureleadersummit.org
              </div>
              <div>
                <v-icon size="small" class="mr-1">fa-envelope</v-icon>
                futureleadersummit[at]gmail.com
              </div>
              <div>
                <v-icon size="small" class="mr-1">fa-phone</v-icon>
                081 2525 29921 (Kiki)
              </div>
              <v-btn
                v-for="icon in icons"
                :key="icon.name"
                icon
                outline
                :href="icon.link"
                class="mx-3">
                <v-icon size="24px">{{ icon.name }}</v-icon>
              </v-btn>
            </v-flex>
            <v-flex class="pa-3" md4>
              <p class="subheading">TENTANG</p>
              <div>
                Future Leader Summit (FLS) merupakan konferensi nasional pemuda tahunan yang digagas oleh Nusantara Muda sejak 2011.
              </div>
            </v-flex>
            <v-flex class="pa-3" md4>
              <v-card flat>
                <v-card-text>
                  <div class="subheading">
                    Dapatkan Info Terbaru dari Kami
                  </div>
                  <v-text-field
                    name="input-1"
                    label="First Name"></v-text-field>
                  <v-text-field
                    name="input-2"
                    label="Last Name"></v-text-field>
                  <v-text-field
                    name="input-3"
                    label="Email"></v-text-field>
                  <v-btn color="primary" block depressed>Subscribe</v-btn>
                </v-card-text>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card-text>
      <v-card-actions class="silver justify-center">
        &copy; {{ new Date().getUTCFullYear() }} — <a href="https://github.com/creativefls/"><strong>CreativeFLS</strong></a>
      </v-card-actions>
    </v-card>
  </v-footer>
</template>
<script>
export default {
  data: () => ({
    icons: [
      { name: 'fa-facebook', link: 'https://facebook.com/FutureLeaderSummit' },
      { name: 'fa-twitter', link: 'https://twitter.com/flsummit' },
      { name: 'fa-instagram', link: 'https://instagram.com/flsummit' },
      { name: 'fa-youtube-play', link: 'https://youtube.com/user/FLSummit' },
    ]
  })
}
</script>

<style lang="stylus" scoped>
.card
  width 100%

.footer
  .container
    display flex
    flex-wrap wrap
    align-items center
</style>
