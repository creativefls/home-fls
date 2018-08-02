<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <br class="my-2">
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
                        <vue-recaptcha
                          ref="recaptcha"
                          @verify="onVerify"
                          @expired="onExpired"
                          :sitekey="sitekey">
                        </vue-recaptcha>
                        <center>
                          <br>
                        <v-btn @click="submit">submit</v-btn>
                        <v-btn @click="clear">clear</v-btn>
                        </center>
                    </form>
                  </v-layout>
                </v-container>
        </v-card-text>
      </v-card>
      
      <br class="my-4">
    </v-flex>
  </v-layout>
</template>


<script>

import Vue from 'vue'
import VeeValidate from 'vee-validate'
import VueRecaptcha from 'vue-recaptcha'

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
        this.$validator.validateAll()
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

