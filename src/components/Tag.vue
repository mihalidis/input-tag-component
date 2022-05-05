<template>
  <span class="tag" :style="{'color':`#${textColor}`, 'background': `#${backgroundColor}`}">
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
    textColor: {
      type: String,
    },
    backgroundColor: {
      type: String,
    }
  },
  methods: {
    removeTag(tagIndex) {
      this.$emit("removeTag", tagIndex);
    }
  }
}
</script>

<style>
.tag {
  font-family: 'Roboto', sans-serif;
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
  border-radius: 10px;
  top: -2px;
  right: 2px;
  width: 8px;
  height: 8px;
  cursor: pointer;
}
.tag .tag-close:after {
  content: '\d7';
}

.tag-content {
  padding: 0 5px 0 0;
}
</style>