<template>
  <v-layout class="fullheight">
    <countdown v-show="showCountdown" :time="eventTime * 1000">
      <template slot-scope="props">
        Time Remaining：{{ props.days }} days, {{ props.hours }} hours, {{ props.minutes }} minutes, {{ props.seconds }} seconds.
      </template>
    </countdown>
  <v-btn @click="showCountdown = !showCountdown">klik</v-btn>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      eventTime: 0,
      showCountdown: false
    }
  },
  created () {
    this.$nextTick(() => {
      this.eventTime = this.$moment('2018-07-01 12:00:00').unix() - this.$moment().unix()
    })
  }
}
</script>
