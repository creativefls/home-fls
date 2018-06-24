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
            <v-btn color="primary" @click="submitMessage" block round depressed>kirim</v-btn>
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
      topic: 'general'
    }
  },
  computed: {
    showSubscribe () {
      if (this.topic != 'general') return false
      return true
    }
  },
  methods: {
    submitMessage () {
      this.$validator.validateAll().then((result) => {
        if(!result) {
          swal(
            'Error',
            'Sepertinya input yang kamu masukkan ada kesalahan',
            'error'
          )
        } else {
          this.$axios.post('http://localhost:3001/api/messages', {
          // this.$axios.post('http://128.199.72.101:3001/api/messages', {
            fullName: this.guestFullName,
            email: this.guestEmail,
            message: this.guestMessage,
            isSubscribe: this.checkboxNewsletter,
            nickName: this.guestNickName,
            topic: this.topic
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
