<script>
import MovieCard from "../components/MovieCard.vue";

export default {
  name: "MovieListPage",
  props: ["movies"],
  emits: ["handleViewDetail"],
  components: { MovieCard },
  methods: {
    handleClickCard(title) {
      this.$emit("handleViewDetail", title);
    },
  },
};
</script>
<template>
  <div class="flex flex-col items-center space-y-2">
    <span class="text-lg font-black">Movie List</span>
    <div class="flex flex-row space-x-3">
      <MovieCard
        :movie="movie"
        @handleViewDetail="handleClickCard"
        v-for="movie in movies"
      />
    </div>
  </div>
</template>

<style></style>
