<template>
  <div class="artist-input__container">
    <input
      class="artist-search__input"
      type="text"
      placeholder="Search your artist"
      @input="filterArtist"
    />
    <button class="artist-input__btn" @click="addArtist">Add Artist</button>
    <div v-if="showArtist === true">
      <input
        class="add-artist__input"
        type="text"
        v-model="artistName"
        placeholder="Artist Name"
        :class="{ invalid: errors.artistName && touched.artistName }"
        @blur="touched.artistName = true"
        @input="validateArtistName"
      /><br />
      <span v-if="errors.artistName && touched.artistName" class="error">{{
        errors.artistName
      }}</span>
      <input
        class="add-artist__input"
        type="text"
        v-model="aboutArtist"
        placeholder="About Artist"
        :class="{ invalid: errors.aboutArtist && touched.aboutArtist }"
        @blur="touched.aboutArtist = true"
        @input="validateAboutArtist"
      /><br />
      <span v-if="errors.aboutArtist && touched.aboutArtist" class="error">{{
        errors.aboutArtist
      }}</span>
      <input
        class="add-artist__input"
        type="text"
        v-model="imgUrl"
        placeholder="Image URL"
        :class="{ invalid: errors.imgUrl && touched.imgUrl }"
        @blur="touched.imgUrl = true"
        @input="validateImgUrl"
      /><br />
      <span v-if="errors.imgUrl && touched.imgUrl" class="error">{{
        errors.imgUrl
      }}</span>
      <button
        class="artist-input__btn"
        @click="addYourArtist"
        :disabled="hasErrors"
      >
        Add
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      // Here is a model.
      artists: {},
      showArtist: false,
      artistName: "",
      aboutArtist: "",
      imgUrl: "",
      errors: {
        artistName: "",
        aboutArtist: "",
        imgUrl: "",
      },
      touched: {
        artistName: false,
        aboutArtist: false,
        imgUrl: false,
      },
    };
  },
  methods: {
    filterArtist(event) {
      const filterValue = event.target.value;
      this.$emit("filter-search", filterValue);
    },

    addArtist() {
      this.showArtist = !this.showArtist;
    },

    addYourArtist() {
      if (!this.hasErrors) {
        console.log({
          artistName: this.artistName,
          aboutArtist: this.aboutArtist,
          imgUrl: this.imgUrl,
        });
      } else {
        return;
      }
      this.artist = {
        name: this.artistName,
        about: this.aboutArtist,
        url: this.imgUrl,
        id: `__id-${Math.floor(Math.random() * 1_000_000)}`,
      };

      console.log(this.artist);
      this.$emit("artist", this.artist);
      this.refreshInput();
    },

    refreshInput() {
      this.artistName = "";
      this.aboutArtist = "";
      this.imgUrl = "";
    },

    validateArtistName() {
      if (!this.artistName.trim()) {
        this.errors.artistName = "Artist name is required.";
      } else if (this.artistName.length < 3) {
        this.errors.artistName =
          "Artist name must be at least 3 characters long.";
      } else {
        this.errors.artistName = "";
      }
    },
    validateAboutArtist() {
      if (!this.aboutArtist.trim()) {
        this.errors.aboutArtist = "About artist is required.";
      } else if (this.aboutArtist.length < 5) {
        this.errors.aboutArtist =
          "About artist must be at least 5 characters long.";
      } else {
        this.errors.aboutArtist = "";
      }
    },
    validateImgUrl() {
      const urlPattern = /^(http|https):\/\/[^ "]+$/;
      if (!this.imgUrl.trim()) {
        this.errors.imgUrl = "Image URL is required.";
      } else if (!urlPattern.test(this.imgUrl)) {
        this.errors.imgUrl = "Please enter a valid URL.";
      } else {
        this.errors.imgUrl = "";
      }
    },
  },
  computed: {
    hasErrors() {
      return (
        !this.artistName ||
        !this.aboutArtist ||
        !this.imgUrl ||
        Object.values(this.errors).some((error) => error !== "")
      );
    },
  },
};
</script>

<style>
#app {
  color: #0f0f00;
}
span {
  display: block;
}
</style>
