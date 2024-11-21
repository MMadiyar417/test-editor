<template>
    <div 
      :contenteditable="true" 
      class="editable-text" 
      @input="updateText"
    >      <span v-if="!text" >
        <slot />
      </span>
      <span v-else v-html="text" />
    </div>
  </template>
  
  <script>
  export default {
    props: {
      value: {
        type: String,
        default: '', 
      },
    },
    data() {
      return {
        text: this.value,
      };
    },
    watch: {
      value(newValue) {
        this.text = newValue;
      },
    },
    methods: {
      updateText(event) {
        this.$emit('update:value', event.target.innerHTML);
      },
    },
  };
  </script>
  
  <style scoped>
  .editable-text {
    padding: 10px;
    min-height: 30px;
    border: 1px solid #ddd;
    margin-bottom: 10px;
  }
  
  .placeholder {
    color: #aaa;
  }
  </style>
  