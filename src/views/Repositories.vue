<template>
  <div class="container">
    <div v-if="loaded">
      <div class="repo-list" v-for="repo in repositories" :key="repo.id">
        <card :repo="repo"></card>
      </div>
    </div>
    <div v-else>
      <content-loader class="content-loader"></content-loader>
      <content-loader class="content-loader"></content-loader>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "@/components/Card.vue";
import ContentLoader from "@/components/ContentLoader.vue";

export default {
  components: {
    Card,
    ContentLoader
  },
  data() {
    return {
      repositories: []
    };
  },
  computed: {
    loaded: function() {
      return this.repositories.length > 0;
    }
  },
  methods: {
    fetchRepositories: async function() {
      try {
        const username = this.$route.params.username;
        const response = await axios.get(
          `https://api.github.com/users/${username}/repos`
        );
        this.repositories = response.data;
      } catch (error) {
        this.repositories = [];
      }
    }
  },
  mounted: function() {
    this.fetchRepositories();
  }
};
</script>

<style lang="scss" scoped>
.content-loader {
  margin: auto;
  display: block;
  width: 100%;
  @media screen and (min-width: 768px) {
    width: 50%;
  }
}

.container {
  margin-top: 6rem;
  margin-bottom: 3rem;
}

.repo-list {
  margin: 1rem auto 0 auto;
  width: 50%;
}
</style>
