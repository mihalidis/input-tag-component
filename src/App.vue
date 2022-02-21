<template>
  <Tags v-model="tags" color="pink"/>
</template>

<script>
import Tags from "./components/Tags";
export default {
  name: "App",
  components: {
    Tags
  },
  data() {
    return {
      tags: "tag1,tag2,tag3,tag4"
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400&display=swap');
@import './assets/theme.css';

body {
  font-family: 'Roboto', sans-serif;
}
</style>


