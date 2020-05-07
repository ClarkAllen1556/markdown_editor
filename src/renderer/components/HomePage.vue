<template>
  <div>
    <div>
      <b-container fluid='xl'>
        <b-row>
          <div>
            <h1>Markdown Editor</h1>
          </div>
        </b-row>
        <b-row>
          <b-col cols="auto">
            <Editor />
          </b-col>
          <b-col cols="auto">
            <Sidebar />
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
  import Editor from "./Editor.vue";
  import Sidebar from "./Sidebar.vue";

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