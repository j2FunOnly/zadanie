<template>
  <div id="app">
    <Editor />
  </div>
</template>

<script>
import Editor from "./components/Editor";

export default {
  name: "App",
  components: {
    Editor
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
