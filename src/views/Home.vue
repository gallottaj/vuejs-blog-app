<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p v-for="post in posts"> {{post.title}}</p>
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