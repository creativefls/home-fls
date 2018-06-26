<template>
  <v-container>
    <v-layout justify-center>
      <v-flex md6>
        <v-card>
          <v-card-text>
            <div class="title">
              {{ customTitle ? customTitle : 'Tinggalkan Pesan' }}
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
            <v-text-field v-model="topic"></v-text-field>
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
              v-if="showSubscribe"
              label="Kabari melalui email"
              v-model="checkboxNewsletter"
              ></v-checkbox>
            <v-btn color="primary" @click="validateSubmitMessage" block round depressed>kirim</v-btn>
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import swal from 'sweetalert2'

export default {
  layout: 'clean',
  data () {
    return {
      checkboxNewsletter: false,
      customTitle: null,
      guestFullName: '',
      guestNickName: '',
      guestEmail: '',
      guestMessage: '',
      topic: ''
    }
  },
  computed: {
    showSubscribe () {
      if (this.topic != 'general') return false
      return true
    }
  },
  methods: {
    validateSubmitMessage () {
      this.$validator.validateAll().then((result) => {
        if(!result) {
          swal(
            'Error',
            'Sepertinya input yang kamu masukkan ada kesalahan',
            'error'
          )
        } else {
          this.submitMessage()
        }
      })
    },
    submitMessage () {
      this.$axios.post('http://128.199.72.101:3001/api/messages', {
        fullName: this.guestFullName,
        email: this.guestEmail,
        message: this.guestMessage,
        isSubscribe: this.checkboxNewsletter,
        nickName: this.guestNickName,
        topic: this.topic
      }).then(response => {
        swal('Success', 'Pesan berhasil kami terima. Jika menghendaki pesan interaktif, kamu bisa menghubungi contact person yang tersedia. Terima kasih ^_^', 'success' ).then(result => {
          if(result.value) window.location.href = '/pesan'
        })
        console.log('sukses, ', response)
      }).catch(error => {
        swal('Error', error.message, 'error' )
        console.log('error, ', error)
      })
    }
  },
  created () {
    let query = this.$route.query
    if (query.fullName) this.guestFullName = query.fullName
    if (query.nickName) this.guestNickName = query.nickName
    if (query.email) this.guestEmail = query.email
    if (query.customTitle) this.customTitle = query.customTitle
    this.$nextTick(() => {
      if (query.topic) {
        this.topic = query.topic
      } else {
        this.topic = 'general'
      }
    })
  }
}
</script>
