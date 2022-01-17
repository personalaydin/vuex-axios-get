<template>
  <div id="app">
    <Posts />
    <Comments />
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import Comments from "./components/Comments";
import Posts from "./components/Posts";

export default {
  name: "App",
  components: {
    Comments,
    Posts,
  },
};

const axiosInstance = axios.create({
  baseURL: "https://jsonplaceholder.typicode.com/",
});

Vue.prototype.$axios = axiosInstance;
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: aquamarine;
}
</style>
