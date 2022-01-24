<template>
  <div style="padding:1em">
  
    <!-- <h1>{{ msg }}</h1> -->
    <b-container class="bv-example-row">
        <b-row>
            <b-col style="textAlign:right">
                <img src="https://www.w3schools.com/howto/img_avatar.png" alt="user" />
            </b-col>
            <b-col cols="8" style="textAlign:right">
                <textarea v-model="comment" style="width:100%" id="message" placeholder="Enter coment"/>
                <p style="position:absolute">Everyone can reply</p>
                <b-button v-on:click="addToPosts(comment)" variant="primary">Post</b-button>
            </b-col>
        </b-row>
    </b-container>
  </div>
</template>

<script>

export default {
  name: 'NewPost',
  props: {
    msg: String,
    addToPosts: Function
  },
  data() {
    return {
      comment: ''
    };
  },
  computed: {
    get_Message() {
      return this.message
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  img {
    width: 70px;
    border-radius: 50%;
  }

</style>
