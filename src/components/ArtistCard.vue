<template>
  <ul class="card__container">
    <li v-for="artist in artists" :key="artist.id">
      {{ artist.name }} {{ artist.about }}
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
};
</script>

<style>
#app {
  color: #0f0f00;
}
</style>
