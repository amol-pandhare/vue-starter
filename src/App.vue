<template>
  <div id="app">
    <NewPostScreen :addToPosts="addPost"/>
    <blog-list :posts="posts" :deleteItem="deletePost"/>
  </div>
</template>

<script>
import BlogList from './components/BlogList.vue'
import NewPostScreen from './components/NewPostScreen.vue'

export default {
  name: 'App',
  methods: {
    addPost(post) {
      // console.log("add to posts list " + post)
      this.posts.unshift({
          id: ++this.noOfPosts,
          logo: '',
          comment: post,
          user: 'Media ABC',
          category: 'CommandPost',
          elapsedTime: '10m',
          likes: 2
        })
    },
    deletePost(postID) {
      // console.log(postID);
      let delID;
      for(let i=0;i<this.posts.length;i++) {
        if(this.posts[i].id === postID) {
          delID = i;
        }
      }
      this.posts.splice(delID, 1);
    }
  },
  components: {
    NewPostScreen,
    BlogList
  },
  data() {
    return {
      noOfPosts: 2,
      posts: [
        {
          id: 2,
          logo: '',
          comment: 'Testing the comment',
          user: 'Dynamic Media',
          category: 'PheonixWorld',
          elapsedTime: '10m',
          likes: 2
        },
        {
          id: 1,
          logo: '',
          comment: ' Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.',
          user: 'User Codegen',
          category: 'Obscene',
          elapsedTime: '30m',
          likes: 0
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 2em;
}
</style>
