<template>
  <vue-markdown v-if="loaded" class="container" :source="content"></vue-markdown>
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
    }
  },
  props: {
    params: {
      type: Object,
      default: "Vue!"
    }
  },
  data() {
    return {
      content: ""
    };
  },
  methods: {
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
.container {
  padding: 1rem;
  width: 100%;
  @media screen and (min-width: 768px) {
    width: 50%;
  }
  margin: 6rem auto 0 auto;
}
</style>
