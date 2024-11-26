<template>
  <div class="artist-input__container">
    <input
      class="artist-search__input"
      type="text"
      placeholder="Search your artist"
    />
    <button class="artist-input__btn" @click="addArtist">Add Artist</button>
    <div v-if="showArtist === true">
      <input
        class="add-artist__input"
        type="text"
        v-model="artistName"
        placeholder="Artist Name"
        required
      /><br />
      <input
        class="add-artist__input"
        type="text"
        v-model="aboutArtist"
        placeholder="About Artist"
        required
      /><br />
      <input
        class="add-artist__input"
        type="text"
        v-model="imgUrl"
        placeholder="Image URL"
        required
      /><br />
      <button class="artist-input__btn" @click="addYourArtist">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      // Here is a model.
      artists: [],
      showArtist: false,
      artistName: "",
      aboutArtist: "",
      imgUrl: "",
    };
  },
  methods: {
    addArtist() {
      this.showArtist = !this.showArtist;
    },

    addYourArtist() {
      this.artists.push({
        name: this.artistName,
        about: this.aboutArtist,
        url: this.imgUrl,
      });

      console.log(this.artists);

      this.refreshInput();
    },

    refreshInput() {
      this.artistName = "";
      this.aboutArtist = "";
      this.imgUrl = "";
    },
  },
};
</script>

<style>
#app {
  color: #0f0f00;
}
</style>
