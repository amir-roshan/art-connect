<template>
  <ul class="card__container">
    <li v-for="artist in artists" :key="artist.id">
      <img :src="artist.url" :alt="`Image of ${artist.name}.`" />
      {{ artist.name }} {{ artist.about }}
      <button @click="() => deletArtist(artist.id)">DELETE</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "ArtistCard",
  props: {
    artists: {
      type: Array,
      required: true,
    },
  },
  methods: {
    deletArtist(id) {
      const artist = this.artists.find((artist) => artist.id === id);
      this.$emit("delete-artist", artist);
    },
  },
};
</script>

<style>
#app {
  color: #0f0f00;
}
</style>
