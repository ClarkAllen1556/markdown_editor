<template>
  <b-container fluid>
    <mavon-editor :toolbars="toolbar" :language="langauge" v-on:save="save"/>
  </b-container>
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
          undo: true,
          redo: true,
          trash: false,
          save: true,
          navigation: true,
          alignleft: true,
          aligncenter: true,
          alignright: true,
          subfield: true,
          preview: true
        }
      };
    },
    methods: {
      save(value, render) {
        const fs = require('fs');
        const { dialog } = require('electron').remote;

        dialog.showSaveDialog().then( res => {
          console.info(res);
          fs.writeFileSync(res.filePath, value);
        }).catch( e => {
          console.error(new Error(e));
        })
      }
    }
  };
</script>

<style scoped>
.mavonEditor {
  width: 100%;
  height: 100%;
}
</style>