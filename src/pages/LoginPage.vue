<script>
export default {
  name: "LoginPage",
  emits: ["loginHandler"],
  props: ["title"],
  data() {
    return {
      login: {
        username: "",
        password: "",
      },
    };
  },
  methods: {
    handleSubmit() {
      console.log("submit");

      this.$emit("loginHandler", this.login.username, this.login.password);
    },
  },
};
</script>

<template>
  <div class="flex flex-col items-center space-y-2">
    <span class="text-lg font-bold">{{ title }}</span>
    <form
      @submit.prevent="handleSubmit"
      class="flex flex-col items-center space-y-2"
    >
      <input
        class="px-3 py-2 border border-blue-300 rounded-lg"
        v-model="login.username"
        placeholder="username"
      />
      <input
        class="px-3 py-2 border border-blue-300 rounded-lg"
        v-model="login.password"
        placeholder="password"
      />
      <button
        class="px-3 py-2 bg-gray-200 border rounded-lg border-blue-500 drop-shadow-lg"
        type="submit"
      >
        Submit
      </button>
    </form>
  </div>
</template>

<style></style>
