<template>
  <div class="home">
    <search-input
      @enter="search"
      v-model="username"
      placeholder="Enter GitHub Username"
      style="margin-right: 10px"
    ></search-input>
    <vue-button @click="search">search</vue-button>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchInput from "@/components/SearchInput.vue";
import Button from "@/components/Button.vue";

export default {
  name: "home",
  components: {
    SearchInput,
    VueButton: Button
  },
  data() {
    return {
      username: ""
    };
  },
  methods: {
    search() {
      if (!this.username) {
        return;
      }
      this.$router.push({
        name: "user",
        params: { username: this.username }
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.home {
  padding: 1rem;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>