<template>
  <v-container fluid>
    <img src="/images/background-unyu.png" class="bg-hero" alt="">
    <fls-hero></fls-hero>
    <v-layout class="fullheight" align-center justify-center>
        <v-flex md10 text-xs-center>
            <div class="subtitle mb-4 py-4 black--text">
                Faye Simanjuntak menjadi sosok yang inspiratif, saat usianya masih 12 tahun, ia 
                mendirikan Rumah Faye, yaitu organisasi nirlaba yang fokus pada isu perdagangan anak.
                 Kini, di usianya yang sudah menginjak 16 tahun ia semakin membuktikan bahwa usia muda 
                 bukan menjadi penghalang untuk menjad`i agen perubahan.
                <br>
            </div>
            <div class="black--text">
                <h1 class="display-2">
                    FAYE SIMANJUNTAK                    
                </h1>
                <img class="pembicara" src="/images/ga_pembicara1.png">
                <h3 class="display-1">
                    Co-Founder Rumah Faye                    
                </h3>
            </div>
        </v-flex>
    </v-layout>
    <!-- <img src="/images/background-tangan.png" class="img-tangan" width="80%" alt="" style="margin-bottom: -40px; margin-left: 120px"> -->
    <v-layout justify-center class="bg-success white--text">
        <v-flex md10 text-xs-center>
            <br class="my-2">
            <div class="subtitle mb-4 py-4 black--text">
                Iman Sjafei adalah salah pelaku industri kreatif di Indonesia, pernah berkarya 
                menjadi seorang jurnalis, kini Ia melebarkan sayap menjadi CEO dari <i>Asumsi.co</i> sebuah 
                platform media online serta menjadi CFO dari <i>Rekreasi.co</i> yang merupakan <i>creative 
                agency nasional</i>.
                <br>
            </div>
            <div class="black--text">
                <h1 class="display-2">
                    IMAN SJAFEI                    
                </h1>
                <img class="pembicara" src="/images/ga_pembicara2.png">
                <h1 class="display-1">
                    CEO of <i>Asumsi.co</i> dan CFO of <i>Rekreasi.co</i>                    
                </h1>
            </div>
            <img src="/images/background-tangan.png" class="img-tangan" width="80%" alt="" style="margin-bottom: -40px; margin-left: 120px">            
        </v-flex>
    </v-layout>
    <v-layout 
        v-for="pembicara in pembicara_rooms" 
        :key="pembicara.title"
        :style="{ backgroundColor: pembicara.bgColor }"
        justify-center 
        class="white--text">
            <v-flex md10 text-xs-center>
                <br class="my-2">
                <div class="display-2 mb-4 py-4 white--text">
                    {{ pembicara.title }}
                    <br>
                </div>
                <div class="black--text" xs6>
                    <h1 class="display-2">
                        {{ pembicara.name }}
                    </h1>
                    <img class="pembicara" :src="pembicara.image">
                    <h1 class="display-1">
                        {{ pembicara.description }}
                    </h1>    
                </div>
                <img :src="pembicara.tangan" class="img-tangan" width="80%" alt="" style="margin-bottom: -40px; margin-left: 120px">            
            </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import FlsHero from '@/components/sections/Hero'

export default {
  components: { FlsHero },
  data () {
    return {
        pembicara_rooms: [
            {
                title: 'ROOM HUMAN CAPITAL',
                image: '/images/hc_pembicara1.png',
                name: 'AGUNG BENZHARIE',
                description: 'CEO & Co-Founder Warung Pintar',
                bgColor: '#3883c7',
                tangan: '/images/background-tangan.png'
            },
            {
                title: 'ROOM POVERTY',
                image: '/images/pov_pembicara1.png',
                name: 'YOHANES SUGIHTONONUGROHO',
                description: 'CEO & Co-Founder Crowde',
                bgColor: '#FFA726',
                tangan: '/images/background-tangan.png'
            },
            {
                title: 'ROOM URBAN PLANING',
                image: '/images/up_pembicara1.png',
                name: 'MARCO WIJAYAKUSUMA',
                description: 'Founder dan Direktur RUJAK Center For Urban Studies',
                bgColor: '#6D4C41',
                tangan: '/images/background-tangan.png'
            },
            {
                title: 'ROOM EDUCATION',
                image: '/images/edu_pembicara1.png',
                name: 'WINASTWAN GORA SWAJATI',
                description: 'Founder Kelase.com',
                bgColor: '#FF7043',
                tangan: '/images/background-tangan.png'
            },
            {
                title: 'ROOM DIGITAL',
                image: '/images/dig_pembicara1.png',
                name: 'TEGUH HARMANDA',
                description: 'COO Tokocrypto',
                bgColor: '#FFEE58',
                tangan: '/images/background-tangan.png'
            },
            {
                title: 'ROOM ENTREPRENEURSHIP',
                image: '/images/ent_pembicara1.png',
                name: 'RANI SOEBIJANTORO',
                description: 'Co-Founder Bookabuku',
                bgColor: '#69F0AE',
                tangan: ''
            },
        ]
    }
  },
  computed: {
  },
  methods: {
  },
}
</script>

<style lang="stylus" scoped>
img.line-barcode {
  width auto
  height 256px
}

img.pembicara {
  height 256px
  border-radius 50%
  border solid 5px black 
}
.section-insta
  position relative
  background: #2ecc71;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #2def7e, #2ecc71);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #2def7e, #2ecc71); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

.follow
  padding 40px
.card > *
  display block
  margin 0 auto

.bg-room1
  background-color: #3883c7

.bg-room2
  background-color #FFA726

.bg-room3
  background-color #6D4C41

.bg-room4
  background-color #FF7043

.bg-room5
  background-color #FFEE58

.bg-room6
  background-color #69F0AE

.bg-hero
  // background: url('/images/background-unyu.png') top center no-repeat
  // background-size: cover
  min-width 100vw
  position absolute
  top: 0
  z-index -1

</style>
