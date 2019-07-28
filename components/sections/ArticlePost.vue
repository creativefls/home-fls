<template>
  <v-container v-show="title" grid-list-md>
    <h1 class="display-2 text-xs-center py-4 white--text">{{ title }}</h1>
    <v-layout wrap>
      <v-flex md4 v-for="(post, index) in posts" :key="post.id">
        <v-card>
          <v-card-media :src="thumbnail[index]" height="200px">
          </v-card-media>
          <v-card-title primary-title class="pb-1">
            <div>
              <h3 class="headline">{{ post.title.rendered }}</h3>
            </div>
            <div> <v-icon>event</v-icon> {{ post.date | moment("MMMM D, YYYY")  }}</div>
          </v-card-title>
          <v-card-text>
            <div v-html="post.excerpt.rendered.substring(0,150)+'...'"></div>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn flat color="primary" :href="post.link">Selengkapnya</v-btn>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>

  </v-container>
</template>

<script>
export default {
  data () {
    return {
      title: 'Artikel',
      posts: [],
      thumbnail: []
    }
  },
  methods: {
    fetchPosts () {
      this.$axios.get('https://futureleadersummit.org/artikel/wp-json/wp/v2/posts', {
        params: {
          per_page: 3
        }
      }).then(response => {
        this.posts = response.data
        let promises = []
        this.posts.forEach(async (post) => {
          promises.push(this.getThumbnail(post.featured_media))
        })
        Promise.all(promises).then(values => {
          console.log('janji semua ', values);
          this.thumbnail = values
        })
        this.title = 'Artikel'
      }).catch(error => {
        console.log(error.message);
      })
    },
    getThumbnail (mediaId) {
      console.log(mediaId, 'mulai humb')
      return new Promise((resolve, reject) => {
        this.$axios.get('https://futureleadersummit.org/artikel/wp-json/wp/v2/media/' + mediaId)
          .then(response => {
            console.log(mediaId, 'dapat humbn')
            resolve(response.data.media_details.sizes.medium.source_url)
          })
          .catch(error => {
            console.log(error.message);
          })
      })
    }
  },
  created () {
    this.fetchPosts()
  }
}
</script>

