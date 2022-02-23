<template>
  <Tags v-model="tags" :color="theme"/>
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
      tags: "tag1,tag2,tag3,tag4",
      theme: 'pink'
    }
  }
}
</script>


