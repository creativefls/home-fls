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
                        <v-checkbox
                            v-validate="'required'"
                            v-model="checkbox"
                            :error-messages="errors.collect('checkbox')"
                            value="1"
                            label="Option"
                            data-vv-name="checkbox"
                            type="checkbox"
                            required
                        ></v-checkbox>

                        <v-btn @click="submit">submit</v-btn>
                        <v-btn @click="clear">clear</v-btn>
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

  Vue.use(VeeValidate)

  export default {
    $_veeValidate: {
      validator: 'new'
    },

    data: () => ({
      name: '',
      email: '',
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4'
      ],
      checkbox: null,
      dictionary: {
        attributes: {
          email: 'E-mail Address'
          // custom attributes
        },
        custom: {
          name: {
            required: () => 'Name can not be empty',
            max: 'The name field may not be greater than 10 characters'
            // custom messages
          },
          select: {
            required: 'Select field is required'
          }
        }
      }
    }),

    mounted () {
      this.$validator.localize('en', this.dictionary)
    },

    methods: {
      submit () {
        this.$validator.validateAll()
      },
      clear () {
        this.name = ''
        this.email = ''
        this.select = null
        this.checkbox = null
        this.$validator.reset()
      }
    }
  }
</script>

