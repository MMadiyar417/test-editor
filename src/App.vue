<template>
  <div id="app">
    <div class="editor-container">
      <MainContent/> 
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import MainContent from './components/MainContent.vue';

export default defineComponent({
  name: 'App',
  components: {
    MainContent
  }
});
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.editor-container {
  margin-top: 20px;
}
</style>
