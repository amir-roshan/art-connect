<template>
  <ul class="card__container">
    <li v-for="artist in artists" :key="artist.id">
      <img :src="artist.url" :alt="`Image of ${artist.name}.`" />
      {{ artist.name }} {{ artist.about }}
      <button @click="() => deletArtist(artist.id)">DELETE</button>
    </li>
    <li v-if="artists.length === 0">
      <h2>Oh no, your artist is not found :(</h2>
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

img {
  display: block;
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin: 10px auto;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

img:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
}

li {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 8px;
  margin-bottom: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

li:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
}

li img {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #ccc;
}

li button {
  margin-left: auto;
  padding: 5px 10px;
  background-color: #ff4d4d;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

li button:hover {
  background-color: #e60000;
}

.card__container {
  width: 30%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px;
  justify-content: center;
  background-color: #f9f9f9;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin: auto;
}
</style>
