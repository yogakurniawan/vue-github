<template>
  <vue-markdown class="container" :source="content"></vue-markdown>
</template>

<script>
import VueMarkdown from "vue-markdown";
import axios from "axios";

export default {
  components: {
    VueMarkdown
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
        debugger;
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
  margin-top: 6rem;
}
</style>
