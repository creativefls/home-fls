<template>
  <v-footer height="auto">
    <v-layout>
      <v-flex>
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
              <v-layout justify-center wrap class="text-xs-center">
                <v-flex class="pa-3" md4>
                  <p class="subheading">HUBUNGI KAMI</p>
                  <div>
                    <v-icon size="small" class="mr-1">fa-envelope</v-icon>
                    info@futureleadersummit.org
                  </div>
                  <div>
                    <v-icon size="small" class="mr-1">fa-envelope</v-icon>
                    futureleadersummit@gmail.com
                  </div>
                  <div>
                    <v-icon size="small" class="mr-1">fa-phone</v-icon>
                     0812 3246 8417 (Anggi)
                  </div>
                  <div>
                    <v-icon size="small" class="mr-1">fa-phone</v-icon>
                    0856 4199 2151 (Girindra)
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
                  <p class="subheading">TENTANG KAMI</p>
                  <div>
                    Future Leader Summit (FLS) merupakan konferensi nasional pemuda tahunan yang digagas oleh Nusantara Muda sejak 2011.
                  </div>
                </v-flex>
                <v-flex class="pa-3" md4>
                  <v-card flat>
                    <v-card-text>
                      <div class="subheading">
                        Tinggalkan Pesan
                      </div>
                      <v-text-field
                        v-model="guestFullName"
                        :error-messages="errors.collect('fullName')"
                        v-validate="'required'"
                        data-vv-name="fullName"
                        data-vv-as="Nama Lengkap"
                        label="Nama lengkap"></v-text-field>
                      <v-text-field
                        v-model="guestNickName"
                        :error-messages="errors.collect('nickName')"
                        v-validate="'required'"
                        data-vv-name="nickName"
                        data-vv-as="Nama Panggilan"
                        label="Nama Panggilan"></v-text-field>
                      <v-text-field
                        v-model="guestEmail"
                        :error-messages="errors.collect('email')"
                        v-validate="'required|email'"
                        data-vv-name="email"
                        data-vv-as="Email"
                        label="Email"></v-text-field>
                      <v-text-field
                        v-model="guestMessage"
                        :error-messages="errors.collect('message')"
                        v-validate="'required'"
                        data-vv-name="message"
                        data-vv-as="Pesan"
                        textarea
                        rows="3"
                        :counter="400"
                        label="Pesan"></v-text-field>
                      <v-checkbox
                        label="Kabari melalui email"
                        v-model="checkboxNewsletter"
                        ></v-checkbox>
                      <v-btn color="primary" @click="submitMessage" block round depressed>kirim</v-btn>
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
      </v-flex>
    </v-layout>
  </v-footer>
</template>

<script>
import swal from 'sweetalert2'

export default {
  data: () => ({
    checkboxNewsletter: false,
    guestFullName: '',
    guestNickName: '',
    guestEmail: '',
    guestMessage: '',
    icons: [
      { name: 'fa-facebook', link: 'https://facebook.com/FutureLeaderSummit' },
      { name: 'fa-twitter', link: 'https://twitter.com/flsummit' },
      { name: 'fa-instagram', link: 'https://instagram.com/flsummit' },
      { name: 'fa-youtube-play', link: 'https://youtube.com/user/FLSummit' },
    ]
  }),
  methods: {
    submitMessage () {
      this.$validator.validateAll().then((result) => {
        if(!result) {
          swal(
            'Error',
            'Sepertinya input yang kamu masukkan ada kekurangan. Silakan dicek kembali ya',
            'error'
          )
        } else {
          this.$axios.post('https://api.futureleadersummit.org/messages', {
            fullName: this.guestFullName,
            email: this.guestEmail,
            message: this.guestMessage,
            nickName: this.guestNickName
          }).then(response => {
            swal(
              'Success',
              'Pesan berhasil kami terima. Jika menghendaki pesan interaktif, kamu bisa menghubungi contact person yang tersedia. Terima kasih ^_^',
              'success'
            )
            console.log('sukses, ', response)
          }).catch(error => {
            swal(
              'Error',
              'Sistem error',
              'error'
            )
            console.log('error, ', error)
          })
        }
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
.card
  width 100%

// .footer
//   .container
//     display flex
//     flex-wrap wrap
//     align-items center
</style>
