<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
@import "~normalize.css/normalize.css";
*,
::before,
::after {
  background-repeat: no-repeat; /* 1 */
  box-sizing: border-box; /* 2 */
}
#app {
  font-family: "Asap", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #24292e;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
