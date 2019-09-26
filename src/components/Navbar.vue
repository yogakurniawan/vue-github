<template>
  <div class="navbar">
    <div class="container">
      <button>
        <img src="../assets/home.png" />
      </button>
      <span class="title">{{ name }}'s Projects</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  img {
    width: 30px;
    margin-right: 1rem;
  }
}

.navbar {
  position: fixed;
  z-index: 32;
  width: 100%;
  top: 0;
  left: 0;
  text-align: center;
  padding: 16px;
  background-color: #24292e;
}

.title {
  font-size: 1.5rem;
  font-weight: bold;
  letter-spacing: 2px;
  line-height: 1.5;
  color: #ffffff;
}
</style>
