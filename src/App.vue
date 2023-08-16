<script>
import LoginPage from "./views/LoginPage.vue";
import MovieListPage from "./views/MovieListPage.vue";
import axios from "axios";

export default {
  data() {
    return {
      movieList: [],
      currentPage: "login",
    };
  },
  components: { LoginPage, MovieListPage },
  created() {
    if (localStorage.getItem("access_token")) {
      this.currentPage = "movieList";
    } else {
      this.currentPage = "login";
    }
  },
  methods: {
    async handleLogin(username, password) {
      try {
        console.log("ini dari app", username, password);

        const { data } = await axios({
          method: "POST",
          url: "http://localhost:3000/users",
          data: {
            username: username,
            password: password,
          },
        });

        console.log(data);

        localStorage.setItem("access_token", "asdfasdf");

        this.currentPage = "movieList";
      } catch (err) {
        console.log(err);
      }
    },
    async handleFetchMovies() {
      try {
        const { data } = await axios({
          method: "GET",
          url: "http://localhost:3000/movies",
        });
        console.log(data);
        this.movieList = data;
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<template>
  <LoginPage v-if="currentPage === 'login'" @handleLogin="handleLogin" />
  <MovieListPage
    v-else-if="currentPage === 'movieList'"
    :movieListDariApp="movieList"
    @handleFetchMoviesDariApp="handleFetchMovies"
  />
</template>

<style></style>
