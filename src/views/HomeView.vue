<script>
  import axios from "axios";

  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js!",
        posts: [],
        articles: [],
      };
    },
    created: function () {
      axios.get("https://jsonplaceholder.typicode.com/posts").then(response => {
        console.log(response.data);
        this.posts = response.data;
      });

      // axios.get("https://newsapi.org/v2/top-headlines?country=us&apiKey=____").then(response => {
      //   console.log(response.data);
      //   this.articles = response.data;
      // });

      axios.get("/articles").then((response) => {
        console.log(response.data);
        this.articles = response.data;
      });
    },
    methods: {},
  };
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
    <div v-for="article in articles" :key="article.title">
      <h2>{{ article }}</h2>
    </div>
  </div>
</template>

<style></style>