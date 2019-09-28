<template>
  <div class="container">
    <div v-if="loaded" class="responsive">
      <div class="repo-list" v-for="repo in repositories" :key="repo.id">
        <card :repo="repo"></card>
      </div>
    </div>
    <div class="content-loader responsive" v-else>
      <content-loader></content-loader>
      <content-loader></content-loader>
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
.responsive {
  margin: auto;
  width: 100%;
  @media screen and (min-width: 768px) {
    width: 50%;
  }
}

.content-loader {
  display: block;
}

.container {
  margin: 6rem auto 3rem auto;
  padding: 1rem;
}

.repo-list {
  margin: 1rem auto 0 auto;
}
</style>
