<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <div class="container">
      <div class="row">
        <div class="col-sm-4" v-for="post in posts">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">id: {{ post.id }}</h5>
              <h5 class="card-title">title: {{ post.title }}</h5>
              <p class="card-text">body: {{ post.body }}</p>
              <img v-bind:src="post.image" width="100px">
              <!-- go to the show page -->
              <a v-bind:href="'/#/posts/' + post.id" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
</style>

<script>

var axios = require('axios');
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      posts: []
    };
  },
  created: function() {
    axios.get('http://localhost:3000/api/posts').then(function(response) {
      console.log(response.data);
      this.posts = response.data;
    }.bind(this));
  },
  methods: {},
  computed: {}
};
</script>