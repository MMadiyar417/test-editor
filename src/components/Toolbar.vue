<template>
  <div class="toolbar">
    <IconButton :onClick="goBack">
      <img src="@/assets/icons/back-icon.svg" alt="Back" />
    </IconButton>
    <IconButton :onClick="goForward">
      <img src="@/assets/icons/forward-icon.svg" alt="Forward" />
    </IconButton>
    <IconButton :onClick="makeHeader">
      <img src="@/assets/icons/heading-icon.svg" alt="Header" />
    </IconButton>
    <IconButton @click="makeParagraph">
      <img src="@/assets/icons/paragraph-icon.svg" alt="Paragraph" />
    </IconButton>
    <IconButton @click="chooseImage">
      <img src="@/assets/icons/image-icon.svg" alt="Image" />
    </IconButton>
    <IconButton :onClick="copy" class="copy_link"> 
        Скопировать HTML
    </IconButton>

  </div>
</template>

<script>
import IconButton from './IconButton.vue';

export default  {
  components: { IconButton },
  methods: {
    goBack() {
      console.log('Назад');
    },
    goForward() {
      console.log('Вперед');
    },
    makeHeader() {
      document.execCommand('formatBlock', false, '<h1>');
    },
    makeParagraph() {
      document.execCommand('formatBlock', false, '<p>');
    },
    chooseImage() {
      const url = prompt('Введите URL изображения');
      if (url) {
        this.$emit('update:imageUrl', url); 
      }
    },
    copy() {
    const html = document.documentElement.outerHTML;
    navigator.clipboard.writeText(html)
    .then(() => {
      alert('Весь HTML-документ скопирован в буфер обмена.');
    })
    .catch((err) => {
      console.error('Ошибка при копировании:', err);
      alert('Не удалось скопировать HTML.');
    });
},
  }}
</script>

<style scoped>
.toolbar {
  display: flex;
  gap: 10px;
}
.copy_link{
    color: #639EFF;
}
</style>
