<script>
export default {
  name: "MovieCard",
  props: ["movie"],
  emits: ["handleViewDetail"],
  methods: {
    viewDetail(title) {
      this.$emit("handleViewDetail", title);
    },
  },
};
</script>

<template>
  <div
    @click="viewDetail(movie.title)"
    class="flex flex-col border border-blue-300 rounded-lg p-4 w-44"
  >
    <img :src="movie.imgSrc" :alt="movie.id" />
    <span class="text-center font-light">{{ movie.title }}</span>
  </div>
</template>
