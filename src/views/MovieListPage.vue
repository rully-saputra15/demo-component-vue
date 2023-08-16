<script>
import MovieCard from "../components/MovieCard.vue";

export default {
  name: "MovieListPage",
  props: ["movieListDariApp"],
  emits: ["handleFetchMoviesDariApp"],
  components: { MovieCard },
  created() {
    this.$emit("handleFetchMoviesDariApp");
  },
};
</script>
<template>
  <div class="flex flex-col items-center space-y-2">
    <span class="text-lg font-black">Movie List</span>
    <div class="flex flex-row space-x-3 flex-wrap">
      <MovieCard
        v-for="movie in movieListDariApp"
        :key="movie.id"
        :movieDariMovieListPage="movie"
      />
      <!-- <div
        v-for="movie in movieListDariApp"
        class="flex flex-col border border-blue-300 rounded-lg p-4 w-44"
        :key="movie.id"
      >
        <img :src="movie.imgSrc" />
        <span class="text-center font-light">{{ movie.title }}</span>
      </div> -->
    </div>
  </div>
</template>

<style></style>
