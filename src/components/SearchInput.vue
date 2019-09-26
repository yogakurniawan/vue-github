<template>
  <div class="search-container">
    <input
      @input="$emit('input', $event.target.value)"
      @keyup.enter="$emit('enter')"
      class="search-input"
      :value="value"
      v-bind="$attrs"
    />
    <span class="search-icon">
      <svg
        class="ml-4 bg-red-500 rounded p-2 h-10 w-12 fill-current text-white"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        width="24"
        height="24"
      >
        <path
          class="heroicon-ui"
          d="M16.32 14.9l5.39 5.4a1 1 0 0 1-1.42 1.4l-5.38-5.38a8 8 0 1 1 1.41-1.41zM10 16a6 6 0 1 0 0-12 6 6 0 0 0 0 12z"
        />
      </svg>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ""
    }
  }
};
</script>

<style lang="scss" scoped>
.search-container {
  position: relative;
  height: 54px;
  width: 50%;
}

.search-icon {
  position: absolute;
  right: 10px;
  top: 15px;
}

.search-input {
  border-radius: 0.25rem;
  border: 1px solid rgba(0, 0, 0, 0.06);
  background: #ffffff;
  width: 100%;
  font-size: 17.5px;
  line-height: 1;
  padding: 1rem 2rem 1rem 0.75rem;
  letter-spacing: 0.2875px;
  z-index: 2;
  margin: 0;
  background-color: #ffffff;
  &:focus {
    outline: none;
  }
  &::-webkit-scrollbar {
    display: none;
  }
  &::placeholder {
    color: #c4c4c4;
  }
}
</style>