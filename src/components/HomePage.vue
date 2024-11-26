<template>
  <AddArtist @artists="handleArtistsData" />
  <ArtistCard :artists="artists" />
</template>

<script>
import AddArtist from "./AddArtist";
import ArtistCard from "./ArtistCard";
export default {
  name: "HelloWorld",
  data() {
    return {
      artists: [
        {
          name: "John Doe",
          about: "A talented musician",
          url: "https://randomuser.me/api/portraits/med/men/32.jpg",
          id: "__id-123456",
        },
        {
          name: "Jane Smith",
          about: "A prolific painter known for abstract art",
          url: "https://randomuser.me/api/portraits/med/women/8.jpg",
          id: "__id-789012",
        },
        {
          name: "Alice Johnson",
          about: "An emerging digital artist specializing in 3D animations",
          url: "https://randomuser.me/api/portraits/med/women/12.jpg",
          id: "__id-3456278",
        },
        {
          name: "Mark Lee",
          about: "A photographer with a keen eye for landscape photography",
          url: "https://randomuser.me/api/portraits/med/men/12.jpg",
          id: "__id-90212134",
        },
      ],
    };
  },
  components: {
    AddArtist,
    ArtistCard,
  },
  methods: {
    handleArtistsData(receivedArtists) {
      this.artists.push(receivedArtists);
      console.log("data arrived:", this.artists);
    },
  },
};
</script>

<style>
#app {
  color: #0f0f00;
}
</style>
