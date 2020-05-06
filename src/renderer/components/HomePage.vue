<template>
  <b-container fluid >
    <b-row>
      <b-col> <h1> Vuepress Markdown Editor </h1> </b-col>
    </b-row>
    <b-row>
      <b-col>
        <Editor />
      </b-col>
      <b-col>
        <Sidebar />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import Editor from './Editor.vue';
import Sidebar from './Sidebar.vue';

export default {
  components: {
    Editor,
    Sidebar
  }
};
</script>

<style scoped>
.container-fluid {
  margin-top: 20px;
}
</style>