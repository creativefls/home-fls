<template>
<v-layout column>
  <timeline>
    <timeline-title>title</timeline-title>
    <timeline-item bg-color="#9dd8e0">
            <v-flex xs12 sm8 md6> 
                <v-card>
                <v-chip style="margin-top: -16px;" class="ml-4" label color="urban" text-color="white">
                <div class="subheading">
                    <v-icon medium class="white--text">event</v-icon>
                    <b>FLS 2011</b>
                </div>
                </v-chip>
                <v-card-text>
                <v-container fluid grid-list-lg>
                        <v-layout row>
                            <v-flex xs7>
                            <div>
                                <div class="headline grey">11 Mei 2011</div>                        
                                <div class="headline"><b>"We are not talking about change, We are making change."</b></div><br>
                                <div>
                                <b class="txt-urban">1</b> Hari 
                                <b class="txt-urban">6</b> Isu 
                                <b class="txt-urban">14</b> Pembicara
                                </div>
                                <div>
                                <b class="txt-urban">224</b> Peserta 
                                <b class="txt-urban">517</b> Pendaftar
                                </div>                        
                            </div>
                            </v-flex>
                            <v-flex xs5>
                            <v-card-media
                                src="https://futureleadersummit.org/2017/assets/img/kilas/2011.png"
                                height="125px"
                                contain
                            ></v-card-media>
                            </v-flex>
                        </v-layout>
                        </v-container>
                </v-card-text>
            </v-card>
        </v-flex>
    </timeline-item>
    <timeline-item :hollow="true">item2</timeline-item>
  </timeline>
</v-layout>
</template>

<script>
import { Timeline, TimelineItem, TimelineTitle } from 'vue-cute-timeline'

export default {
  components: {
    Timeline,
    TimelineItem,
    TimelineTitle
  }
}
</script>

<style lang="stylus">
.card
  border-radius 12px
  box-shadow 0 2px 12px 0 rgba(0,0,0,.1)
  &.fls-form-group
    .card__title
      padding-bottom 0
    .card__text
      padding-top 0
  .chip--label
    border-bottom-left-radius inherit
    border-bottom-right-radius inherit
</style>
