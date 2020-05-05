<template>
  <b-container fluid class="ctn">
    <div>
      <h1> Vuepress Markdown Editor </h1>
    </div>
    <div>
      <Editor> </Editor>
    </div>
  </b-container>
</template>

<script>
import Editor from './Editor.vue';

export default {
  components: {
    Editor
  }
};
</script>

<style scoped>
.container-fluid {
  margin-top: 20px;
}
</style>