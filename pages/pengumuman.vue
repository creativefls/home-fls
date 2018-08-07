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

                          <!-- <vue-recaptcha
                            v-validate="'required'"
                            data-vv-as="captcha"
                            ref="recaptcha"
                            @verify="onVerify"
                            @expired="onExpired"
                            :sitekey="sitekey">
                          </vue-recaptcha> -->
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
      getRoomImageUrl (room) {
        switch (room) {
          case 'Education':
            return 'https://user-images.githubusercontent.com/21119252/41973205-85ec42bc-7a3e-11e8-9a29-e3f296080e21.png'
          case 'Digital':
            return 'https://user-images.githubusercontent.com/21119252/41973182-71436b92-7a3e-11e8-9d7e-8f039c0e67e3.png'
          case 'Poverty':
            return 'https://user-images.githubusercontent.com/21119252/41973269-aa219768-7a3e-11e8-8e77-6023aef4d135.png'
          case 'Human Capital':
            return 'https://user-images.githubusercontent.com/21119252/41973250-a087b4e4-7a3e-11e8-845b-ec4c8c38d34f.png'
          case 'Entrepreneurship':
            return 'https://user-images.githubusercontent.com/21119252/41973233-91527996-7a3e-11e8-9b1c-34e2b8ee0118.png'
          case 'Urban Planning':
            return 'https://user-images.githubusercontent.com/21119252/41973340-e2cc96bc-7a3e-11e8-8a25-a079c0b6e279.png'
          default:
            return 'https://user-images.githubusercontent.com/21119252/41821836-c2787e10-7810-11e8-8d2a-cc829bea4ae3.png'
        }
      },
      submit () {
      this.$validator.validateAll().then((result) => {
        if(!result) {
          swal(
            'Error',
            'Sepertinya input yang kamu masukkan ada kekurangan. Silakan dicek kembali ya',
            'error'
          )
        } else {
          this.$axios.get('http://128.199.72.101:3000/api/Registrars/findOne', {
            //email from v-model text-field
            params: { 
              filter: {
                where: { email: this.email } 
              }
            }
          }).then(response => {
            console.log('data, ',response);
            if (response.data.acceptanceStatus == 2) {
              swal({
                title: '<h6>WELCOME TO FUTURE LEADER SUMMIT 2018!</h6>',
                width: 650,
                imageUrl: 'https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png',
                imageWidth: 150,
                html: 
                  `<strong>Dear, <strong>${response.data.fullname}</strong> dari <strong>${response.data.province}</strong> !</strong> <br> ` +
                  `<p>  </p>` +
                  `<strong>Setelah melewati tahap seleksi, kami mengucapkan selamat karena kamu telah terpilih menjadi <br> Delegates Future Leader Summit 2018 di Room <strong>${response.data.roomFirst}</strong></strong>` +
                  `<p>  </p>` +
                  // `<center><img src="getRoomImageUrl(${response.data.roomFirst})" class="room-Pengumuman"></img><center>` +             
                  `<strong>Mari mulai ambil bagian untuk perubahan dunia bersama 239 pemuda-pemudi terbaik Indonesia di konferensi Future Leader Summit yang diselenggarakan di <strong>Semarang</strong> tanggal <strong>8-9 September 2018</strong> mendatang. </strong>`+
                  `<p>  </p>` +                                    
                  `<p>Silahkan cek emailmu untuk informasi selanjutnya!</p>` +
                  `<p>Terima Kasih </p>`
              }) 
            } else if (response.data.acceptanceStatus == 1) {
              swal({
                width: 650,
                imageUrl: 'https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png',
                imageWidth: 150,
                html: 
                  `<strong>Dear, <strong>${response.data.fullname}</strong> dari <strong>${response.data.province}</strong> !</strong> <br> ` +
                  `<p>  </p>` +
                  `<strong>Terima kasih karena sudah mau memulai mengambil bagian untuk perubahan dunia dengan mendaftarkan dirimu di Future Leader Summit 2018.</strong>` +
                  `<p>  </p>` +
                  `<strong>Saat ini, kamu berada di posisi <strong>WAITING LIST</strong> delegates Future Leader Summit 2018 untuk Room <strong>${response.data.roomFirst}</strong>.</strong>` +           
                  `<p>  </p>` +                  
                  `<strong>Apabila ada delegasi room bersangkutan yang mengundurkan diri, maka panitia FLS 2018 akan menghubungi kamu untuk keterangan lebih lanjut.</strong>`+
                  `<p>  </p>` +                                    
                  `<p>Silahkan cek emailmu untuk informasi selanjutnya!</p>` +
                  `<p>Terima Kasih </p>`
              }) 
            } else {
              swal({
                width: 650,
                imageUrl: 'https://user-images.githubusercontent.com/21119252/34459239-16407fee-ee1d-11e7-94c1-dc6446f962b0.png',
                imageWidth: 150,
                html: 
                  `<strong>Dear, <strong>${response.data.fullname}</strong> dari <strong>${response.data.province}</strong> !</strong> <br> ` +
                  `<p>  </p>` +
                  `<strong>Terima kasih karena sudah berpartisipasi dan mau mencoba untuk ambil bagian dalam merubah dunia dengan mendaftarkan dirimu di Future Leader Summit 2018.</strong>` +
                  `<p>  </p>` +
                  `<strong>Namun kami meminta maaf, karena untuk saat ini, kamu belum bisa bergabung menjadi salah satu delegasi di Future Leader Summit 2018 . </strong>` +           
                  `<p>  </p>` +                  
                  `<strong>Jangan putus asa dan tetap semangat ya! Masih banyak cara lainnya untuk ikut serta mengambil bagian dalam mengubah dunia.</strong>`+
                  `<p>  </p>` +                                    
                  `<p>Sampai jumpa di lain kesempatan!</p>`
              }) 
            }
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
      onVerify (response) {
        this.loginForm.pleaseTickRecaptchaMessage = '';
        this.loginForm.recaptchaVerified = true;
        console.log('Verify: ' + response)
      },
      onExpired () {
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

<style>
  .room-Pengumuman{
    width: 200px;
  }
</style>
