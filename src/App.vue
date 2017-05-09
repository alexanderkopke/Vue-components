<template>
  <div id="app">
    <div class="container-fluid">
    <ul>
    <post :post="post" v-for="post in posts"  :key="post.title"></post>
    </ul>
    <div id="comment-box">
    <div class="input-group">
        <input type="text" class="form-control" placeholder="Enter a comment..." v-model="comment" @keyup.enter="postComment">
        <span class="input-group-btn">
        <button class="btn btn-primary" type="button" @click="postComment">Submit</button></span>
    </div>
  </div>
    </div>
  </div>
</template>
<script>
import Post from './components/Post.vue'
export default {
  name: 'app',
  data () {
    return {
     posts: [
          { title: "A post for the reddit demo starting at 15 votes",
          votes: 15},
          {
            title: "Try out the upvoting, it works, I promise",
            votes: 63
          },
          {
            title: "Alexander rules some kind of world", 
            votes: 118
          }
     ],
     comment:''
    }
  },
  methods:{
    postComment(){
      this.posts.push({
        title: this.comment,
        votes: 0
      })
      this.comment = ''
    }
  },
  components:{'post': Post}
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
  margin-top: 60px;
  width: 600px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;

}

a {
  color: #42b983;
}

</style>
