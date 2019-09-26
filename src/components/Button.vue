<template>
  <button v-on="$listeners" class="button">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.button {
  font-family: inherit;
  transition: all 0.3s;
  position: relative;
  border: 1px solid transparent;
  user-select: none;
  text-transform: uppercase;
  font-size: 0.875rem;
  white-space: nowrap;
  line-height: 1.5;
  padding-bottom: calc(0.375em - 1px);
  padding-left: 0.75em;
  padding-right: 0.75em;
  padding-top: calc(0.375em - 1px);
  border-radius: 0.25rem;
  text-align: center;
  vertical-align: middle;
  font-weight: bold;
  height: 54px;
  letter-spacing: 1.5px;
  box-shadow: none;
  color: #ffffff;
  background-color: #000000;
  border-color: transparent;
  &:hover,
  &:focus {
    text-decoration: none;
  }
  &:focus,
  &:active {
    outline: 0;
  }
  &:not(:disabled):not(.disabled) {
    cursor: pointer;
  }
  &:disabled {
    background-color: #dadada;
    border-color: #dadada;
  }
  &:hover {
    transition: all 0.2s;
    box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.25);
    transform: translateY(-2px);
  }
}
</style>