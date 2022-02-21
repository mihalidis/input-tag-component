<template>
  <span class="tag" :class="selectedTheme">
    <span class="tag-content">{{ tag }}</span>
    <span class="tag-close" @click.prevent="removeTag(index)"></span>
  </span>
</template>

<script>
export default {
  name: "Tag",
  props: {
    tag: {
      type: String,
      default: '...loading'
    },
    index: {
      type: [Number, String],
      default: 0
    },
    tagTheme: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      selectedTheme: "pink"
    }
  },
  created() {
    if(this.tagTheme) {
      this.selectedTheme = this.tagTheme;
    }
  },
  methods: {
    removeTag(tagIndex) {
      this.$emit("removeTag", tagIndex);
    }
  }
}
</script>

<style scoped>
.tag {
  position: relative;
  border-radius: 4px;
  cursor: default;
  font-size: 14px;
  margin-right: 6px;
  padding: 6px 8px;
  height: 28px;
}

.tag .tag-close {
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4px;
  border-radius: 10px;
  top: -5px;
  right: -4px;
  width: 8px;
  height: 8px;
  cursor: pointer;
}

.tag .tag-close:after {
  content: '\d7';
}
</style>