<template>
  <div>
    <navbar :name="$route.params.username"></navbar>
    <router-view />
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  components: {
    Navbar
  }
};
</script>

<style lang="scss" scoped>
</style>
