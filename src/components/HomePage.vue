<template>
  <AddArtist />
  <ArtistCard />
</template>

<script>
import AddArtist from "./AddArtist";
import ArtistCard from "./ArtistCard";
export default {
  name: "HelloWorld",
  data() {
    return {
      // Here is a model.
      msg: "Welcome to Your Vue.js App",
    };
  },
  components: {
    AddArtist,
    ArtistCard,
  },
};
</script>

<style>
#app {
  color: #0f0f00;
}
</style>
