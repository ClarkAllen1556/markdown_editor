<template>
  <div>
    <mavon-editor :toolbars="toolbar" :language="langauge" />
  </div>
</template>

<script>
  import Vue from 'vue';
  import mavonEditor from 'mavon-editor';
  import 'mavon-editor/dist/css/index.css';

  Vue.use(mavonEditor);

  export default {
    name: 'Editor',
    data() {
      return {
        langauge: 'en',
        toolbar: {
          bold: true,
          italic: true,
          header: true,
          underline: true,
          strikethrough: true,
          mark: true,
          superscript: true,
          subscript: true,
          quote: true,
          ol: true,
          ul: true,
          link: true,
          imagelink: true,
          code: true,
          table: true,
          fullscreen: false,
          readmodel: false,
          htmlcode: true,
          help: true,
          /* 1.3.5 */
          undo: true,
          redo: true,
          trash: false,
          save: false,
          /* 1.4.2 */
          navigation: true,
          /* 2.1.8 */
          alignleft: true,
          aligncenter: true,
          alignright: true,
          /* 2.2.1 */
          subfield: true,
          preview: true
        }
      };
    }
  };
</script>

<style scoped>
.mavonEditor {
  width: 100%;
  height: 100%;
}
</style>