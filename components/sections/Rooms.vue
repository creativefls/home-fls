<template>
  <v-layout class="fullheight my-4 py-4 bg-success" align-center>
    <v-flex text-xs-center>
      <!-- <img src="/images/background-tangan.png" class="img-tangan" width="80%" alt="" style="margin-top: -100px;"> -->
      <h1 class="display-3 white--text font-weight-medium">
        Room FLS 2019
      </h1>
      <br class="my-4">
      <v-container>
        <v-layout align-center justify-center wrap>
          <v-flex v-for="room in rooms" :key="room.name" md4 xs6>
            <v-card class="elevation-0 cursor-pointer" color="transparent" @click.native.stop="openRoomInfo(room.name)">
              <v-card-title style="justify-content: center;">
                <img :src="room.image" alt="" width="50%">
              </v-card-title>
              <v-card-text class="white--text">
                <h4 class="title mb-1">{{ room.name }}</h4>
                <p>{{ room.description }}</p>
              </v-card-text>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
      <div class="py-4"></div>
      <!-- <img src="/images/background-tangan.png" class="img-tangan" width="80%" alt="" style="margin-bottom: -40px;"> -->
    </v-flex>
   <v-dialog v-model="dialogRoom" max-width="80%">
      <v-card>
        <v-card-title>
          <div class="headline">{{ selectedRoomInfo.name }}</div>
          <v-spacer></v-spacer>
          <v-icon class="cursor-pointer" @click="dialogRoom = false">close</v-icon>
        </v-card-title>
        <v-card-text>
          <p class="subheading">{{ selectedRoomInfo.description }}</p>
          <p v-html="selectedRoomInfo.longDesc">
          </p>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      rooms: [
        {
          id: 0,
          image: '/images/rooms/Digital.png',
          name: 'Digital',
          color: 'secondary',
          longDesc: `Internet of Things (loT), Artificial Intelegence (Al), guantum computing, augmented reality, big data analytics merupakan beberapa teknologi yang hangat pada era ini. Pertanyaan yang muncul, bagaimana cara kita agar teknologi itu dapat diakses oleh semua orang?`
        },
        {
          id: 1,
          image: '/images/rooms/Education.png',
          name: 'Education',
          color: 'warning',
          longDesc: `Dunia perubahan tengah mengalami perubahan. Menurut Peter Fisk dalam tulisannya mengenai “Education 4.0', terdapat sembilan pergeseran nilai pendidikan yang meliputi: tak berbatas ruang dan waktu, pembelajaran bersifat perseorangan, berbasis data dan pengalaman lapangan, beragam pilihan materi pembelajaran, interpretasi data, perubahan sistem ujian, kemudahan siswa dalam mengatur kurikulumnya, serta pentingnya pendampingan terhadap siswa. Inilah saat pemuda untuk berupaya merespon sembilan tren pergeseran nilai pada sistem pendidikan.`
        },
        {
          id: 2,
          image: '/images/rooms/Environment.png',
          name: 'Environment',
          color: 'error',
          longDesc: `Plastik, polusi, illegal logging adalah beberapa masalah yang timbul dari eksploitasi manusia terhadap lingkungan. Ketidakseimbangan terjadi antara manusia dan alam. Tujuan dari platform ini adalah membangun lingkungan hidup yang berkembang secara koheren dengan peradapan manusia.`
        },
        {
          id: 3,
          image: '/images/rooms/International Relation.png',
          name: 'International Relation',
          color: 'info',
          longDesc: `Dalam visi ASEAN 2025 terdapat beberapa aspek yang menjadi sorotan utama yakni, aspek keamanan politik, ekonomi dan sosial budaya. Pada platform International Relations ini, delegates akan membahas bagaimana pergerakan negara-negara ASEAN pada saat ini dan hingga tahun 2025 dalam era revolusi industri 4.0 serta mencari solusi rendahnya daya saing Indonesia dibandingkan negara ASEAN.`
        },
        {
          id: 4,
          image: '/images/rooms/Technopreneur.png',
          name: 'Technopreneur',
          color: 'primary',
          longDesc: `Jumlah pengguna internet telah berkembang pesat selama dekade terakhir. Sekarang 407. dari populasi dunia melakukan kegiatan online dan lebih dikenal dengan sebutan netizen. Indonesia dalam kancah persaingan global menurut World Competitiveness Report menempati urutan ke-45 atau terendah dari seluruh negara yang diteliti, di bawah Singapura (8), Malaysia (34), Cina (35), Filipina (38), dan Thailand (40). Salah satu penyebabnya adalah tingginya sifat konsumtif masyarakat. Platform ini bertujuan merubah perilaku masyarakat yang konsumtif ke produktif di sektor teknologi dan ekonomi dalam upaya meninngkatkan daya saing global.`
        },
        {
          id: 5,
          image: '/images/rooms/UrbanPlanning.png',
          name: 'Urban Planning',
          color: 'success',
          longDesc: `Masalah sosial merupakan hal yang kerap menjadi masalah kota-kota besar di Indonesia. Adanya ketidakseimbangan antara kualitas wilayah dengan permintaan akan kebutuhan penduduk menjadi sumber masalahnya. Pada platform ini delegates akan menginisiasi langkah nyata demi tercapainya wilayah pemukiman yang inklusif, aman, tahan lama dan berkelanjutan.`
        },
      ],
      selectedRoom: '',
      dialogRoom: false
    }
  },
  computed: {
    selectedRoomInfo () {
      if (this.selectedRoom.length < 1) return { image: '', name: '', description: '', longDesc: '' }
      return this.rooms.find(room => room.name == this.selectedRoom)
    }
  },
  methods: {
    openRoomInfo (room) {
      this.selectedRoom = room
      this.dialogRoom = true
    }
  }
}
</script>
