<template>
  <Tags v-model="tags" background-color="ff6161" text-color="fff"/>
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
    }
  }
}
</script>


