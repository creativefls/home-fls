<template>
  <v-layout class="fullheight my-4 py-4 bg-success" align-center>
    <v-flex text-xs-center>
      <!-- <div class="py-4" style="background: url('/images/background-tangan.png') bottom center no-repeat; background-size: 100%;"></div> -->
      <img src="/images/background-tangan.png" width="80%" alt="" style="margin-top: -100px;">
      <h1 class="display-3 white--text font-weight-medium">
        Room FLS 2018
      </h1>
      <br class="my-4">
      <v-container>
        <v-layout align-center justify-center wrap>
          <v-flex v-for="room in rooms" :key="room.name" md4 xs6>
            <v-card class="elevation-0" color="transparent">
              <v-card-title style="justify-content: center;">
                <img :src="room.image" alt="">
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
      <img src="/images/background-tangan.png" width="80%" alt="" style="margin-bottom: -40px;">
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      rooms: [
        { image: '/images/rooms/education.png', name: 'Education', description: 'Accessing The Knowledge Easily, Generating Educated People Evenly' },
        { image: '/images/rooms/entrepreneur.png', name: 'Entrepreneur', description: 'Seen the Unseen, Escalate the Oppotunity.' },
        { image: '/images/rooms/poverty.png', name: 'Poverty', description: 'Harnessing Agricultural Potential To Eradicate Poverty.' },
        { image: '/images/rooms/urban-planning.png', name: 'Urban Planning', description: 'The Viable Solution for Sustainable Living.' },
        { image: '/images/rooms/human-capital.png', name: 'Human Capital', description: 'Learning Ability In The Future Human Age.' },
        { image: '/images/rooms/digital.png', name: 'Digital', description: 'Redefining The Next Big Thing of Digital Technology.' }
      ]
    }
  }
}
</script>
