<template>
  <!-- <div v-on:click="click"> -->
    <!-- <h1>{{ msg }}</h1> -->
    <b-card no-body class="mb-1" >
      <b-card-header header-tag="header" class="p-1" role="tab" style="textAlign:right">
        <b-row>
            <b-col cols="2"></b-col>
            <b-col cols="8" style="textAlign:left; paddingTop: 5px"><b>{{post.user}}</b> @{{post.category}} </b-col>
            <b-col><b-button block v-b-toggle="collapse_id" variant="info" size="sm">Arrow</b-button></b-col>
        </b-row>
      </b-card-header>
      <b-collapse :id="collapse_id" visible :accordion="collapse_id" role="tabpanel">
        <b-card-body>
          <b-row>
            <b-col style="textAlign:right">
              <img src="https://www.w3schools.com/howto/img_avatar2.png" alt="ICON" />
            </b-col>
            <b-col cols="10" style="textAlign:left">
                <b-card-text v-show="!isEditing">
                    {{post.comment}}
                </b-card-text>

                <textarea v-model="post.comment" style="width:100%" v-show="isEditing" />

                <b-row style="textAlign:center">
                    <b-col>
                        <b-button size="sm" v-on:click="isEditing=!isEditing">{{isEditing ? 'Save' : 'Edit'}}</b-button>
                    </b-col>
                    <b-col>
                        <b-button size="sm" v-show="!isEditing" v-on:click="deleteItem(post.id)">Delete</b-button>
                    </b-col>
                    <b-col>
                        <b-icon icon="heart" variant="primary" v-on:click="fillLike=!fillLike" v-show="!fillLike && !isEditing"></b-icon>
                        <b-icon icon="heart-fill" variant="primary" v-on:click="fillLike=!fillLike" v-show="fillLike && !isEditing"></b-icon>
                    </b-col>
                </b-row>
            </b-col>
          </b-row>
        </b-card-body>
      </b-collapse>
    </b-card>
</template>

<script>

export default {
  name: 'BlogItem',
  props: {
    msg: String,
    post: Object,
    deleteItem: Function
  },
  data() {
    return {
      isEditing: false,
      fillLike: false,
    }
  },
  computed: {
    collapse_id() {
      return 'accordion-' + this.post.id
    }
  },
  methods: {
    toggleLike: (value) => {
      console.log(value);
      this.fillLike = value;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .card-header {
    background-color: white;
    border-bottom: 0px;
  }
  img {
    width: 70px;
    border-radius: 50%;
  }
</style>
