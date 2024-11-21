<template>
    <div class="editable-image">
      <img v-if="imageSrc" :src="imageSrc" alt="Editable image" />
    </div>
  </template>
  
  <script>
  export default {
    props: {
      imageUrl: {
        type: String,
        default: '',
      },
    },
    computed: {
      imageSrc: {
        get() {
          return this.imageUrl;
        },
        set(value) {
          this.$emit('update:imageUrl', value); 
        },
      },
    },
  };
  </script>
  
  <style scoped>
  .editable-image {
    margin-bottom: 10px;
  }
  .editable-image img {
    max-width: 100%;
    height: auto;
  }
  </style>
  