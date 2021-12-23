<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
const API_KEY = "AIzaSyCXUA_58D6n8sxhwMaE8BeU0rm1f0L4HH8";

export default {
  name: "App",
  components: {
    SearchBar,
  },
  methods: {
    onTermChange: function (searchTerm) {
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params: {
          key: API_KEY,
          type: "video",
          part: "snippet",
          q: searchTerm
        },
      }).then(response => console.log(response));
    },
  },
};
</script>
