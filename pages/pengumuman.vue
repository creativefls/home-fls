<template>
  <v-container fluid>
    <v-layout class="fullheight white--text" column justify-center align-center>
    <h1 class="display-3">
        Pengumuman Delegates
      </h1>
      <div class="subtitle mb-4 py-4">
        Masukkan email yang kamu gunakan untuk mendaftar !
      </div>
      <img src="/images/background-unyu.png" class="bg-hero" alt="">      
      <v-flex md10 text-xs-center>
        <v-card>
          <v-card-text>
            <v-container fluid grid-list-lg>
                    <v-layout row>
                      <form>
                          <v-text-field
                              v-validate="'required|email'"
                              v-model="email"
                              :error-messages="errors.collect('email')"
                              label="E-mail"
                              data-vv-name="email"
                              required
                          ></v-text-field>
                          <br class="my-2">

                          <vue-recaptcha
                            v-validate="'required'"
                            data-vv-as="captcha"
                            ref="recaptcha"
                            @verify="onVerify"
                            @expired="onExpired"
                            :sitekey="sitekey">
                          </vue-recaptcha>
                          <center>
                            <br class="my-1">
                          <v-btn @click="submit" round>submit</v-btn>
                          <v-btn @click="clear" round>clear</v-btn>
                          </center>
                      </form>
                    </v-layout>
                  </v-container>
          </v-card-text>
        </v-card>
        
        <br class="my-4">
      </v-flex>
    </v-layout>
</v-container>
</template>


<script>

import Vue from 'vue'
import VeeValidate from 'vee-validate'
import VueRecaptcha from 'vue-recaptcha'
import swal from 'sweetalert2'

  Vue.use(VeeValidate)
  Vue.use(VueRecaptcha)
  export default {
    $_veeValidate: {
      validator: 'new'
    },

    data: () => ({
      sitekey: '6Le-wvkSAAAAAPBMRTvw0Q4Muexq9bi0DJwx_mJ-', //key sementara dari google 
      email: '',
      loginForm: {
      recaptchaVerified: false,
      pleaseTickRecaptchaMessage: ''
      },
      dictionary: {
        attributes: {
          email: 'E-mail Address'
          // custom attributes
        }
      }
    }),
    components: {
    'vue-recaptcha': VueRecaptcha
    },

    mounted () {
      this.$validator.localize('en', this.dictionary)
    },

    methods: {
      submit () {
      this.$validator.validateAll().then((result) => {
        if(!result) {
          swal(
            'Error',
            'Sepertinya input yang kamu masukkan ada kekurangan. Silakan dicek kembali ya',
            'error'
          )
        } else {
          this.$axios.get('http://128.199.72.101:3000/explorer/', {
            email: this.guestEmail
          }).then(response => {
            swal({
              title: '<h6>WELCOME TO FUTURE LEADER SUMMIT 2018!</h6>',
              width: 650,
              imageUrl: 'https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png',
              imageWidth: 100,
              html: 
                '<strong>Dear, <strong>Nama</strong> <strong>Profinsi</strong> !</strong>' +
                '<p>Setelah melewati tahap seleksi, kami mengucapkan selamat karena kamu telah terpilih menjadi <br> Delegates Future Leader Summit 2018 di Room (Education)</p>' +
                '<p>Mari mulai ambil bagian untuk perubahan dunia bersama 239 pemuda-pemudi terbaik Indonesia di konferensi Future Leader Summit yang diselenggarakan di Semarang tanggal 8-9 September 2018 mendatang. </p>'+
                '<p>Silahkan cek emailmu untuk informasi selanjutnya!</p>' +
                '<p>Terima Kasih </p>'
            })
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
    },
      clear () {
        this.email = ''
        this.$validator.reset()
      },
      onVerify: function (response) {
        console.log('Verify: ' + response)
      },
      onExpired: function () {
        console.log('Expired')
      }
    }
  }
</script>

<style lang="stylus" scoped>

.bg-hero
  // background: url('/images/background-unyu.png') top center no-repeat
  // background-size: cover
  min-width 100vw
  position absolute
  top: 0
  z-index -1

</style>