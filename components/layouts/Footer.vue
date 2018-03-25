<template>
  <v-footer height="auto">
    <v-card flat tile>
      <v-card-title class="primary white--text">
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
      <v-card-text class="grey lighten-3">
        <v-container>
          <v-layout>
            <v-flex
              v-for="(col, i) in rows"
              :key="i"
              xs3
            >
              <span class="body-2" v-text="col.title.toUpperCase()"/>
              <div
                v-for="(child, i) in col.children"
                :key="i"
                v-text="child"
              />
            </v-flex>
            <v-flex xs3 layout column>
              <span class="body-2">CONTACT</span>
              <div>
                <v-icon size="18px" class="mr-3">fa-home</v-icon>
                New York, NY 10012, US
              </div>
              <div>
                <v-icon size="18px" class="mr-3">fa-envelope</v-icon>
                info@example.com
              </div>
              <div>
                <v-icon size="18px" class="mr-3">fa-phone</v-icon>
                + 01 234 567 88
              </div>
              <div>
                <v-icon size="18px" class="mr-3">fa-print</v-icon>
                + 01 234 567 89
              </div>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card-text>
      <v-card-actions class="grey lighten-2 justify-center">
        &copy; {{ new Date().getUTCFullYear() }} — <strong>CreativeFLS</strong>
      </v-card-actions>
    </v-card>
  </v-footer>
</template>
<script>
export default {
  data: () => ({
    icons: [
      { name: 'fa-facebook', link: 'https://google.com' },
      { name: 'fa-twitter', link: '' },
      { name: 'fa-google-plus', link: '' },
      { name: 'fa-linkedin', link: '' },
      { name: 'fa-instagram', link: '' }
    ],
    rows: [
      {
        title: 'Company Name',
        children: ['Here you can use rows and columns here to organize your footer content. Lorem ipsum dolor sit amet, consectetur adipisicing elit']
      },
      {
        title: 'Products',
        children: ['MDBootstrap', 'MDWordPress', 'BrandFlow', 'Bootstrap Angular']
      },
      {
        title: 'Useful Links',
        children: ['Your account', 'Become an Affiliate', 'Shipping Rates', 'Helper']
      }
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
