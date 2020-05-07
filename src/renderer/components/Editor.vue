<template>
  <b-row>
    <mavon-editor :toolbars="toolbar" :language="langauge" v-on:save="save" />
  </b-row>
</template>

<script>
  import Vue from "vue";
  import mavonEditor from "mavon-editor";
  import "mavon-editor/dist/css/index.css";
  import { isNullOrUndefined } from "util";

  Vue.use(mavonEditor);

  export default {
    name: "Editor",
    data() {
      return {
        langauge: "en",
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
        const fs = require("fs");
        const { dialog } = require("electron").remote;

        dialog.showSaveDialog({
          title: "Save markdown post?",
          defaultPath: "*.md",
          message: "Please specify a name for your file and it's location",
          showsTagField: false,
          properties: ["showHiddenFiles", "createDirectory"]
        }).then(res => {
          if (res.canceled) {
            throw new Error(`File not saved; canceled by user.`);
          } else if (isNullOrUndefined(res.filePath)) {
            throw new Error(`FIle not saved; please specify a valid file name.`);
          }
          fs.writeFile(res.filePath, value, e => {
            if (e) throw e;

            alert(`File saved: ${res.filePath}`);
            return res;
          });
        }).catch(e => {
          console.error(new Error(e));
          alert(`Error saving file. File not saved.\n${e}`);
          return e;
        });
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