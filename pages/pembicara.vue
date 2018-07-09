<template>
  <v-container fluid>
    <img src="/images/background-unyu.png" class="bg-hero" alt="">
    <fls-hero></fls-hero>
    <v-layout class="fullheight" align-center justify-center>
        <v-flex md10 text-xs-center>
            <div class="subtitle mb-4 py-4">
                Rhenald Kasali merupakan seorang Guru Besar Ilmu Manajemen di Universitas Indonesia dan 
                juga dikenal sebagai seorang praktisi bisnis yang sangat ulung dan telah menghasilkan 
                banyak sekali tulisan yang menginspirasi banyak orang. Selain itu, beliau juga mendirikan 
                Rumah Perubahan, sebuah yayasan yang bergerak dalam bidang pendidikan, Kesejahteraan sosial, 
                danlingkungan hidup.
                <br>
            </div>
            <h1 class="display-2">
                RHENALD KASALI
            </h1>
            <img src="/images/pembicara1.png">
            <h3 class="display-1">
                Praktisi Bisnis; <br>
                Founder Rumah Perubahan
            </h3>
        </v-flex>
    </v-layout>
    <img src="/images/background-tangan.png" class="img-tangan" width="80%" alt="" style="margin-bottom: -40px; margin-left: 120px">
    <v-layout justify-center class="bg-success white--text">
        <v-flex md10 text-xs-center>
            <br class="my-2">
            <div class="subtitle mb-4 py-4">
                Alamanda Shantika pertama naik melalui karir cemerlangnya di salah satu startup 
                bisnis transportasi di Indonesia sebagai Vice President of Product. Perjalannya berlanjut 
                ketika beliau memutuskan untuk berpindah haluan untuk ikut berpartisipasi dalam membantu 
                para startup muda Indonesia dalam mengembangkan bisnisnya melalui Binar Academy.
                <br>
            </div>
            <h1 class="display-2">
                ALAMANDA SHANTIKA
            </h1>
            <img src="/images/pembicara2.png">
            <h1 class="display-1">
                Founder Binar Academy
            </h1>
            <img src="/images/background-tangan.png" class="img-tangan" width="80%" alt="" style="margin-bottom: -40px; margin-left: 120px">            
        </v-flex>
    </v-layout>    
    <v-layout justify-center class="bg-pembicara3 white--text">
        <v-flex md10 text-xs-center>
            <br class="my-2">
            <div class="subtitle mb-4 py-4">
                Christian Rijanto merupakan seorang pengusaha muda yang sukses dalam grup bisnis 
                miliknya yang bernama ISMAYA GROUP. Peursahaan yang menjalankan usahanya dalam bidang 
                foodand beverage, Clubs, Property and hotel, Event organizer dan juga Music Publishing. 
                Di usiayang masih tergolong produktif ini, beliau telah mencetak banyak prestasi seperti 
                Indonesia'sTop 50 Creative Entrepreneur, Featured on BBC World as Indonesia's Rising 
                Entrepreneur, FortuneMagazine "Top 40 Under 40" dan lain sebagainya.
                <br>
            </div>
            <h1 class="display-2">
                CHRISTIAN RIJANTO
            </h1>
            <img src="/images/pembicara3.png">
            <h1 class="display-1">
                Managing Partner & Founder Ismaya Group
            </h1>
            <br class="my-2">        
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

.bg-pembicara3
  background-color: #3883c7

.bg-hero
  // background: url('/images/background-unyu.png') top center no-repeat
  // background-size: cover
  min-width 100vw
  position absolute
  top: 0
  z-index -1

</style>
