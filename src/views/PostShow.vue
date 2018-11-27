<template>
  <div class="home">
    <div class="col-sm-4">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">title: {{ post.title }}</h5>
          <p class="card-text">body: {{ post.body }}</p>
          <img v-bind:src="post.image" width="100px">
          <a href="/show.html" class="btn btn-primary">Go somewhere</a>
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
      message: "Welcome to Vue.js from the show componenent",
      post: {}
    };
  },
  created: function() {
    console.log(this);
    axios.get('http://localhost:3000/api/posts/' + this.$route.params.id).then(response => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {},
  computed: {}
};
</script>
