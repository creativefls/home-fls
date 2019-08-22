<template>
  <v-layout class="fullheight my-5 pt-5" align-center>
    <v-flex text-xs-center>
      <div style="margin-top: 20em;"></div>
      <h1 class="display-3 success--text font-weight-medium">
        Future Leader Summit
        <br />2019
      </h1>
      <div class="pt-5"></div>
      <v-layout align-center justify-center>
        <v-flex md6>
          <countdown :time="eventTime * 1000">
            <template slot-scope="props">
              <v-layout class="success--text border-count mx-5">
                <v-flex xs3 class="display-2">{{ props.days }}</v-flex>
                <v-flex class="display-2">:</v-flex>
                <v-flex xs3 class="display-2">{{ props.hours }}</v-flex>
                <v-flex class="display-2">:</v-flex>
                <v-flex xs3 class="display-2">{{ props.minutes }}</v-flex>
                <v-flex class="display-2">:</v-flex>
                <v-flex xs3 class="display-2">{{ props.seconds }}</v-flex>
              </v-layout>
              <v-layout class="mt-3 success--text mx-5">
                <v-flex xs3 class="headline">Hari</v-flex>
                <v-flex xs3 class="headline">Jam</v-flex>
                <v-flex xs3 class="headline">Menit</v-flex>
                <v-flex xs3 class="headline">Detik</v-flex>
              </v-layout>
            </template>
          </countdown>
        </v-flex>
      </v-layout>
      <br class="my-4" />
      <br class="my-4" />
      <div class="py-4"></div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      eventTime: 0
    };
  },
  created() {
    this.$nextTick(() => {
      this.eventTime =
        this.$moment("2019-09-20 23:59:59").unix() - this.$moment().unix();
    });
  }
};
</script>
<style>
  .border-count  {
    padding: 2rem 0;
    border: 0.5rem solid white;
    border-radius: 1%;
  }
</style>
