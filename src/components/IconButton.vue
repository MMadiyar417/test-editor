<template>
    <button class="icon-button" @click="handleClick">
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    props: {
      onClick: {
        type: Function,
        required: true,
      },
    },
    methods: {
      handleClick() {
        console.log('Получен onClick пропс:', this.onClick);
        this.onClick();
      },
    },
  };
  </script>
  
  <style scoped>
  .icon-button {
    background: none;
    border: none;
    cursor: pointer;
    padding: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .icon-button:hover {
    background-color: #5d5d5d;
    
  }
  </style>
  