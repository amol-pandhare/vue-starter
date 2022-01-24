<template>
<div>
    <blog-item v-for="post in posts" v-bind:key="post.id" :post="post" :deleteItem="deleteItem"/> </div>
</template>

<script>
import BlogItem from "./BlogItem.vue"


export default {
  name: 'BlogList',
  props: {
    msg: String,
    posts: Array,
    deleteItem: Function
  },
  components: {
    BlogItem
  },
  methods: {
    click: () => {
console.log("clicked");
    },
  test: () => {
console.log("success");
  }}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
