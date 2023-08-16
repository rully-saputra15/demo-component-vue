<script>
export default {
  name: "MovieCard",
  props: ["movieDariMovieListPage"],
};
</script>

<template>
  <div class="flex flex-col border border-blue-300 rounded-lg p-4 w-44">
    <img :src="movieDariMovieListPage.imgSrc" />
    <span class="text-center font-light">{{
      movieDariMovieListPage.title
    }}</span>
  </div>
</template>
