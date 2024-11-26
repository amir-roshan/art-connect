<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      // Here is a model.
      msg: "Welcome to Your Vue.js App",
    };
  },
};
</script>

<style>
#app {
  color: #0f0f00;
}
</style>
