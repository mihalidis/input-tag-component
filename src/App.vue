<template>
<div class="tag-container">
  <div class="tag-wrapper">
      <span class="tag" v-for="(tag, index) in tags" :key="index">
    <span class="tag-content">{{ tag }}</span>
    <span class="tag-close" @click.prevent="removeTag(index)"></span>
  </span>
    <input class="tag-input" type="text" @keypress.enter="handleEnter">
  </div>
  <span v-if="showMessage" class="error-message">{{ errorMessage }}</span>
</div>
</template>

<script>
export default {
  data() {
    return {
      tags: ['test1','test2','test3','test4','test5'],
      errorMessage: 'tag is already exist',
      showMessage: false
    }
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
body {
  font-family: 'Roboto', sans-serif;
}

.tag-container {
  border: 1px solid #ccc;
  padding: 10px 15px;
}

.tag-wrapper {
  margin-bottom: 4px;
}

.tag {
  position: relative;
  background-color: #FFE4C0;
  border-radius: 4px;
  color: #495371;
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
  background-color: #FFBBBB;
  padding: 4px;
  border-radius: 10px;
  top: -5px;
  right: -4px;
  width: 8px;
  height: 8px;
  color: #fff;
  cursor: pointer;
}

.tag .tag-close:after {
  content: '\d7';
}

.tag-input {
  font-family: 'Roboto', sans-serif;
  background-color: #FFE4C0;
  border: none;
  height: 28px;
  border-radius: 4px;
  color: #495371;
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
