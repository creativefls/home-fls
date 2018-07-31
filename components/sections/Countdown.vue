<template>
  <v-layout class="fullheight my-4 py-4" align-center>
    <v-flex text-xs-center>
      <div class="py-4"></div>
      <div class="py-4"></div>
      <v-layout align-center justify-center>
        <v-flex md6>
          <countdown :time="eventTime * 1000">
            <template slot-scope="props">
              <v-layout class="success--text">
                <v-flex xs3 class="display-3"> {{ props.days }} </v-flex>
                <v-flex class="display-3">:</v-flex>
                <v-flex xs3 class="display-3"> {{ props.hours }} </v-flex>
                <v-flex class="display-3">:</v-flex>
                <v-flex xs3 class="display-3"> {{ props.minutes }} </v-flex>
                <v-flex class="display-3">:</v-flex>
                <v-flex xs3 class="display-3"> {{ props.seconds }} </v-flex>
              </v-layout>
              <v-layout class="info--text">
                <v-flex xs3 class="headline"> Hari </v-flex>
                <v-flex xs3 class="headline"> Jam </v-flex>
                <v-flex xs3 class="headline"> Menit </v-flex>
                <v-flex xs3 class="headline"> Detik </v-flex>
              </v-layout>
            </template>
          </countdown>
        </v-flex>
      </v-layout>
      <br class="my-4">
      <h1 class="display-2 info--text font-weight-medium">
        Hingga penutupan pendaftaran FLS 2018
      </h1>
      <br class="my-4">
      <div class="py-4"></div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      eventTime: 0
    }
  },
  created () {
    this.$nextTick(() => {
      this.eventTime = this.$moment('2018-07-31 23:59:00').unix() - this.$moment().unix()
    })
  }
}
</script>
