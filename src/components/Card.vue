<template>
  <a href class="card">
    <div class="repo">{{ repo.name }}</div>
  </a>
</template>

<script>
export default {
  props: {
    repo: {
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.card {
  text-decoration: transparent;
  border-radius: 0.25rem;
  display: block;
  border: 1px solid rgba(0, 0, 0, 0.06);
  overflow: hidden;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  cursor: pointer;
  height: 100%;
  .repo {
    color: #24292e;
    text-align: left;
    font-size: 1.5rem;
    letter-spacing: 0.35px;
    font-weight: bold;
    padding: 1rem 1.5rem;
  }

  &:hover {
    transition: all 0.2s;
    box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.25);
    transform: translateY(-2px);
  }
}
</style>
