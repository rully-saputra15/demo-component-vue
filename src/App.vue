<script>
import LoginPage from "./pages/LoginPage.vue";
import MovieListPage from "./pages/MovieListPage.vue";

import axios from "axios";
export default {
  data() {
    return {
      movies: [],
      currentPage: "login",
    };
  },
  components: { LoginPage, MovieListPage },

  created() {
    if (localStorage.getItem("access_token")) {
      this.currentPage = "movieList";
      this.handleFetchMovies();
    } else {
      this.currentPage = "login";
    }
  },

  methods: {
    async handleLogin(username, password) {
      try {
        const { data } = await axios({
          method: "POST",
          url: "http://localhost:3000/users",
          data: {
            username: username,
            password: password,
          },
        });
        localStorage.setItem("access_token", "blabla");
        this.currentPage = "movieList";
        this.handleFetchMovies();
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
        this.movies = data;
      } catch (err) {
        console.log(err);
      }
    },

    handleViewDetail(title) {
      alert(`Clicked ${title}`);
    },
  },
};
</script>

<template>
  <LoginPage
    v-if="currentPage === 'login'"
    title="Login"
    @loginHandler="handleLogin"
  />
  <MovieListPage
    v-else-if="currentPage === 'movieList'"
    @handleViewDetail="handleViewDetail"
    :movies="movies"
  />
</template>

<style></style>
