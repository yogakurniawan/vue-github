<template>
  <div>
    <navbar></navbar>
    <div class="repo">
      <div class="list" v-for="repo in repositories" :key="repo.id">
        <card :repo="repo"></card>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Navbar from "@/components/Navbar.vue";
import Card from "@/components/Card.vue";

export default {
  components: {
    Navbar,
    Card
  },
  data() {
    return {
      repositories: []
    };
  },
  mounted: async function() {
    try {
      debugger
      const data = await axios.get(`https://api.github.com/users/users/${params.username}/repos`);
      this.repositories = data;
    } catch (e) {
      this.repositories = [];
    }
  }
};
</script>

<style lang="scss" scoped>
.repo {
  display: flex;
  justify-content: center;
  .list {
    width: 50%;
  }
}
</style>
