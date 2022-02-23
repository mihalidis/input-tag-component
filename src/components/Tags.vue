<template>
  <div class="tag-container">
    <div class="tag-wrapper">
      <tag v-for="(tag, index) in tags"
           :key="index"
           :tag="tag"
           :index="index"
           :tag-theme="color"
            @removeTag="removeTag"/>
      <input placeholder="Add tag..." class="tag-input" :class="color" type="text" @keypress.enter="handleEnter">
    </div>
    <span v-if="showMessage" class="error-message">{{ errorMessage }}</span>
  </div>
</template>

<script>
import tag from "./Tag";

export default {
  name: "Tags",
  components: { tag },
  props: {
    value: {
      type: String,
      required: false
    },
    color: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      tags: [],
      errorMessage: 'tag is already exist',
      showMessage: false
    }
  },
  watch: {
    tags() {
      this.$emit("input", this.tags.join(","));
    }
  },
  created() {
    this.tags = this.value.split(",");
  },
  methods: {
    handleEnter(event) {
      const tagText = event.target;

      const tagIndex = this.tags.findIndex(element => {
        return element.toLowerCase() === tagText.value.toLowerCase();
      });

      if(tagIndex === -1) {
        this.tags.push(tagText.value);
      } else {
        this.showMessage = true;
        setTimeout(() => {
          this.showMessage = false
        }, 1500);
      }

      event.target.value = '';
    },
    removeTag(tagIndex) {
      this.tags.splice(tagIndex, 1);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400&display=swap');

.pink {
  background-color: #FFE4C0;
  color: #495371;
}

.pink .tag-close {
  background-color: #FFBBBB;
  color: #fff;
}

.blue {
  background-color: #94DAFF;
  color: #495371;
}

.blue .tag-close {
  background-color: #99FEFF;
  color: #fff;
}
.tag-container {
  border: 1px solid #ccc;
  padding: 10px 15px;
}

.tag-wrapper {
  margin-bottom: 4px;
}

.tag-input {
  font-family: 'Roboto', sans-serif;
  border: none;
  height: 28px;
  border-radius: 4px;
}

.tag-input:focus {
  outline: none !important;
  box-shadow: 0 0 8px #C1F4C5;
}

.error-message {
  font-size: 12px;
  font-style: italic;
  background-color: #EF6D6D;
  color: aliceblue;
  padding: 3px 8px;
  border-radius: 4px;
}
</style>