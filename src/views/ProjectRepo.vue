<template>
  <div v-if="loaded" class="container">
    <div class="link">
      <router-link :to="repositoriesLink">← Back to Repositories</router-link>
    </div>
    <vue-markdown :source="content"></vue-markdown>
  </div>
  <div v-else class="container">
    <content-loader class="content-loader"></content-loader>
    <content-loader class="content-loader"></content-loader>
  </div>
</template>

<script>
import VueMarkdown from "vue-markdown";
import axios from "axios";
import ContentLoader from "@/components/ContentLoader.vue";

export default {
  components: {
    ContentLoader,
    VueMarkdown
  },
  computed: {
    loaded: function() {
      return !!this.content;
    },
    repositoriesLink: function() {
      return `/${this.params.username}`;
    }
  },
  props: {
    params: {
      type: Object
    }
  },
  data() {
    return {
      content: ""
    };
  },
  methods: {
    goToUserPage() {
      this.$router.push({ name: "user" });
    },
    fetchReadme: async function() {
      try {
        const url = `https://api.github.com/repos/${this.params.username}/${this.params.repo}/readme`;
        const response = await axios.get(url);
        this.content = atob(response.data.content);
      } catch (error) {
        this.content = "# No Readme File";
      }
    }
  },
  mounted: function() {
    this.fetchReadme();
  }
};
</script>

<style lang="scss" scoped>
.link {
  margin-bottom: 2rem;
}

.container {
  padding: 1rem;
  width: 100%;
  @media screen and (min-width: 768px) {
    width: 50%;
  }
  margin: 6rem auto 0 auto;
}
</style>
