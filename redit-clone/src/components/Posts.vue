<template>
  <div class="hello mt-3">
    <ul class="list-unstyled">
      <li v-for="(post, i) in posts" v-bind:key="i" class="media m-3">
        <img class="mr-3 thumbnail" :src="post.data.thumbnail" :alt="post.data.title">
        <div class="media-body">
          <h5 class="mt-0 mb-1"><a :href="createRenderUrl(post.data.permalink)" target="_blank">{{post.data.title}}</a></h5>
          <h6 class="text-danger">{{ post.data.ups }} ⬆️</h6>
          <p>Created about {{ fromNow(post.data.created_utc) }} ago by {{ post.data.author }}</p>
          <span class="badge badge-pill badge-secondary">{{ post.data.num_comments }} Comments</span>
          <button class="btn btn-primary btn-sm rounded ml-26" v-if="isImage(post)" @click="post.showImage = !post.showImage">{{ !post.showImage ? 'Show' : 'Hide' }} Image</button>
          <div v-if="post.showImage" class="mt-2">
            <img class="showImage" :src="post.data.url" alt="">
          </div>
          </div>
        </li>
    </ul>
  </div>
</template>

<script>
import fromnow from 'fromnow'

export default {
  name: 'Posts',
  data () {
    return {
      posts: []
    }
  },
  mounted () {
    this.load()
  },
  methods: {
    load () {
      const url = 'https://www.reddit.com/r/rarepuppers/.json'
      fetch(url)
        .then(response => response.json())
        .then((result) => {
          result.data.children = result.data.children.map((child) => ({
            ...child,
            showImage: false
          }))
          this.posts = result.data.children.reverse()
        })
    },
    fromNow (postDate) {
      return fromnow(postDate * 1000)
    },
    createRenderUrl (path) {
      return `https://www.reddit.com${path}`
    },
    isImage (post) {
      return post.data.url.match(/\.(jpg|png|jpeg|bpm)$/)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .thumbnail {
    width: 100px;
    height: 100px;
 }
 .showImage {
    width: 500px;
    height: 500px;
 }
</style>
